<p align="center">
  <a href="https://github.com">too long; didn't read linux from scratch</a>
  <br/>
</p>

---

too long; didn't read linux from scratch.

tldrlfs is a short guide that will teach you how to build a working operating system using the Linux kernel in much fewer commands and less time than LFS. It's meant to inform the reader, but be much more straight to the point in nature. All that's needed is a little bit of time, some hardware to work on, and if you're so inclined, copious amounts of alcohol if you want a fun drinking game.

---

While Linux From Scratch is a great book, it provides a fair bit of unnecessary information to an end user. It is filled to the brim with information, and while that's not at all a bad thing, it is very daunting to readers who wish to only have a minimal operating system. At the bare minimum you only need the kernel and a process that runs as PID 1. _That's it._ Of course, readers probably want a tailored distribution to their needs. Perhaps that's a desktop, a specialized media server -- whatever the case may be, the two components previously mentioned are the greatest common denominator.

This GitHub repository is comprised entirely of README files to guide you through the bare minimum and just a _little_ bit more to get an operating system up and off the ground.

---

Table of Contents -

- [building the kernel](https://github.com/comfies/tldrlfs/tree/master/kernel)
- [installing an init](https://github.com/comfies/tldrlfs/tree/master/init)
- [installing a shell](https://github.com/comfies/tldrlfs/tree/master/shells)
- [installing a bootloader](https://github.com/comfies/tldrlfs/tree/master/bootloaders)
- [core utilities](https://github.com/comfies/tldrlfs/tree/master/coreutils)
- [additional guides](https://github.com/comfies/tldrlfs/)

---

There's only two prerequisites to begin tl;dr lfs.     
(A) An already running Linux distribution to bootstrap from.     
(B) A storage medium to install to.      

The distribution to bootstrap from does not necessarily need to be installed on anything; you can do this from a live medium if you so choose. If you're not comfortable working on real hardware or want to practice, you can always work with a virtual machine.

To prepare you storage medium you will need to partition the disk, format it, and mount it somewhere on your currently running distribution.

```
$ mkdir -p ./tldrlfs
$ fdisk /dev/sdX
$ mkfs.ext4 /dev/sdXY
$ mount /dev/sdXY ./tldrlfs
$ export BUILD_DIR=./tldrlfs
```

`/dev/sdX` and `/dev/sdXY` refers to a device file for a storage medium. Yours may be `/dev/sdb`, `/dev/sdc`, or anything else. If you do not know the path for your device, you can use `lsblk`. `X` refers to the drive itself, and `Y` is the specific partition you wish to use.

You are not at all tied to using `ext4` as your filesystem, `fdisk` for your partitioning program, or otherwise. Keep in mind, this is a guide, not a legally binding contract. Feel free to supplement your own preferences where applicable.

Just remember: have fun!

---

# Contributing
Hey you! Yes you! tl;dr lfs needs help! Feel free to contribute if you find something missing. Remember to read our <a href="https://github.com/comfies/tldrlfs/blob/master/CONTRIBUTING.md">CONTRIBUTING.md</a> before contributing!
