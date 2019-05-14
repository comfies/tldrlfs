# tldrlfs
Too Long; Didn't Read Linux From Scratch

## Preface
Linux From Scratch, while it is a great book, provides a lot of unnecessary information. To get a Linux based operating system off of the ground, you only need two things, Linux, and an init. That's _it_. Of course, you will probably want to tailor your distribution to a specific purpose -- maybe you want a desktop, a specialized media server -- but whatever it may be, the two components mentioned above are the greatest common denominator. This GitHub repository README will guide you through the bare minimum for a running operating system using the Linux kernel, and just a _little_ bit more to make it more usable.

The content that will be covered in this README include the following:
- Building the Linux kernel
- Creating an initramfs
- Installing an implementation of core utilities
- Installing a shell
- Installing an init for the system to use
- Installing a bootloader

Prerequisites:
- An already running Linux install to bootstrap from*
- A storage medium to install to*

* If you don't want to work on actual hardware, you are always able to work from a virtual machine.

If you're ready to begin, go ahead and read on.

# Preparing Storage Medium
