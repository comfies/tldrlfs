# tldrlfs
Too Long; Didn't Read Linux From Scratch

In short, this guide will teach you to build a working operating system that uses the Linux kernel in much fewer commands than LFS. It will take a much smaller amount of time, copious amounts of alcohol if you're so inclined, and plenty of cursing.

## Preface
Linux From Scratch, while it is a great book, provides a lot of unnecessary information. To get a Linux based operating system off of the ground, you only need two things, Linux, and an init. That's _it_. Of course, you will probably want to tailor your distribution to a specific purpose -- maybe you want a desktop, a specialized media server -- but whatever it may be, the two components mentioned above are the greatest common denominator. This GitHub repository README will guide you through the bare minimum for a running operating system using the Linux kernel, and just a _little_ bit more to make it more usable.

The content that will be covered in this guide include the following:
- [Building the Linux kernel](https://github.com/Sweets/tldrlfs/tree/master/kernel)
- [Installing an init for the system to use](https://github.com/Sweets/tldrlfs/tree/master/init)
- [Installing a shell](https://github.com/Sweets/tldrlfs/tree/master/shells)
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
$ mkdir -p $BUILDDIR/boot
```

# Installing an implementation of core utilities

While there are many implementations of core utilities (busybox, toybox, GNU coreutils, ubase, sbase, BSD utils, etc), this guide strives for the most basic bitch of installs. By default anyways. That being said, the choice is obvious: GNU coreutils it is.

Download, extract, configure, build, install. You get the idea by now, it's the same soup, just reheated. That's literally all Linux is -- a bowl of reheated soup.

```
wget https://ftp.gnu.org/gnu/coreutils/coreutils-8.31.tar.xz
tar xf ./coreutils-8.31.tar.xz
cd ./coreutils-8.31
CFLAGS="-static" ./configure --prefix=$BUILDDIR/usr
make
make install
```
