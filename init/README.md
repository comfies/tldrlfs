# Installing an Init for the System to Use

The kernel does not boot into a usable system, rather it starts an init, which is a program dedicated to setting up the system for usage.
There's many inits to choose from, and they all have different reasons as to why you would or would not use them.
Unfortunately, this guide is in its infancy, and so it only provides instructions for one, that being [hummingbird](https://github.com/Sweets/hummingbird).

As a reader, feel free to contribute more to provide more options for others to build on their system.

# Running the init

If there is no early userspace, the kernel will attempt to execute any of `/sbin/init`, `/etc/init`, `/bin/init` (ordered from highest to least precedence).
If no working init is found, the kernel will attempt to execute `/bin/sh`. The kernel will panic if all of these fail.

If the `init` kernel parameter is supplied to the kernel at boot, it will attempt to execute the file at the given path first (see the bootloader section for kernel parameters).

## Init build instructions

- [hummingbird](https://github.com/Sweets/tldrlfs/tree/master/init/hummingbird)
