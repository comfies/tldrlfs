# Source

The linux kernel source can be downloaded from many places, patched or otherwise, but one of the best places to get the kernel source is
[kernel.org](https://kernel.org/). If you're cloning a git repository, `--depth=1` will make the download process a lot quicker.

Regardless of the means of which you get the source, extract the source if necessary, and cd into the directory.

```sh
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.1.tar.xz
tar xf ./linux-5.1.tar.xz
cd ./linux-5.1
```

---

# Preparing

There are multiple methods by which you can configure the kernel, `menuconfig`, `nconfig`, or `config`.
`menuconfig` and `nconfig` both require ncurses.

```sh
make mrproper
make nconfig
```

Or, if you don't want to do any configuring and are OK with the defaults, just use:
```
make defconfig
```

---

# Building

```sh
make
```

Building will take four business days to complete, so you'll probably want to find something else to bide your time until compilation
is complete.

![Compilation time](https://imgs.xkcd.com/comics/compiling.png)

---

# Installation

Once done compiling, you'll copy the kernel image and various configuration files to `/boot` on your medium. Note that the kernel image name must start with `vmlinuz-`, anything afterwards doesn't really matter.

```sh

make install
```

If you wish to use an uncompressed kernel, use the `extract-vmlinux` script provided by the kernel.

#### See the bootloader section for kernel parameters
