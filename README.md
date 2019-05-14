# tldrlfs
Too Long; Didn't Read Linux From Scratch

In short, this guide will teach you to build a working operating system that uses the Linux kernel in much fewer commands than LFS. It will take a much smaller amount of time, copious amounts of alcohol if you're so inclined, and plenty of cursing.

## Preface
Linux From Scratch, while it is a great book, provides a lot of unnecessary information. To get a Linux based operating system off of the ground, you only need two things, Linux, and an init. That's _it_. Of course, you will probably want to tailor your distribution to a specific purpose -- maybe you want a desktop, a specialized media server -- but whatever it may be, the two components mentioned above are the greatest common denominator. This GitHub repository README will guide you through the bare minimum for a running operating system using the Linux kernel, and just a _little_ bit more to make it more usable.

The content that will be covered in this README include the following:
- Building the Linux kernel
- Creating an initramfs
- Installing an init for the system to use
- Installing a shell
- Installing an implementation of core utilities
- Installing a bootloader

Prerequisites:
- An already running Linux install to bootstrap from*
- A storage medium to install to*

\* If you don't want to work on actual hardware, you are always able to work from a virtual machine.

If you're ready to begin, go ahead and read on.

# Preparing Storage Medium

You'll need to create a directory to work in. It can be named anything, but for the purposes of TLDRLFS, it'll be called "build".
Once a build directory has been made you'll need to mount and format your storage medium. Hopefully you don't have anything you need on that medium. TLDRLFS assumes that your device is `/dev/sdb`.

```
$ mkdir -p ./build
$ export BUILDDIR=./build
$ fdisk /dev/sdb # partition the disk (translation, just fuck all the data on the device and make a single partition)
$ mkfs.ext4 /dev/sdb1
$ mount /dev/sdb1 ./build
```

You'll need some additional directories to boot the system and have some usable tools, but for now we'll just need `/boot`.

```
$ mkdir -p ./build/boot
```

# Building the Kernel

You'll need to grab a copy of the kernel. You can clone a git repo or just download a tar, but we'll use tar. `--depth=1` is a life saver here if you have higher level brain functionality and use git.

```
$ wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.1.tar.xz
$ tar xf ./linux-5.1.tar.xz
$ cd ./linux-5.1
```

You'll need to prepare the kernel to be built, configure it, and then build it, in that order. It'll probably take some time.

![Compilation time](https://imgs.xkcd.com/comics/compiling.png)

```
$ make mrproper
$ make nconfig
$ make
```

Once done compiling, you'll copy the kernel image and various configuration files to `/boot` on your medium. Note that the kernel image name must start with `vmlinuz-`, anything afterwards doesn't really matter.

```
$ cp -iv ./arch/x86_64/boot/bzImage $BUILDDIR/boot/vmlinuz-help-im-trapped-inside-this-machine
$ cp -iv System.map $BUILDDIR/boot/System.map
$ cp -iv .config $BUILDDIR/boot/config
```

# Creating an initramfs

An initramfs is a filesystem that the kernel will load into RAM that is then used to mount the real root device and boot it. To create an initramfs cpio image, you will need a dedicated build directory for it. You'll need to create the basic kernel API filesystem, as well as any utilities you'd like to include with the initramfs image (e.g. busybox shell), and a file located in the root named `init` (this is not the same as your system init; this file is executed by the kernel to switch roots into the actual filesystem and load the real init).

```
mkdir -p ./initramfs/{proc,sys,dev,bin}
export INITRAMFS=./initramfs
cd $INITRAMFS
mkdir -p ./mnt/real_root
```

The init file here can be change as necessary for your system, but given that this guide is for those who just want a very basic system, we'll be making a very basic init.

```
cat > ./init << EOF
#!/bin/busybox sh

mount -t devtmpfs none /dev
mount -t proc none /proc
mount -t sysfs none /sys

mkdir /mnt/real_root
mount -o ro /dev/sda1 /mnt/real_root

exec switch_root /mnt/real_root /sbin/init "$@"
EOF
```

Note that the device we're working on (`/dev/sdb`) is referenced as `/dev/sda` in the init file. This is done on purpose because the device will be `/dev/sda` in the context of the kernel loading it as the root device.

With the init file created, you can now generate the cpio image and place it into your boot directory. You should still be within your initramfs build directory.

```
find . | cpio --create --format=newc | gzip --best > $BUILDDIR/boot/initramfs.gz
```

# Installing an init for the system to use
