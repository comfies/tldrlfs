<p align="center">
  <a href="https://github.com">too long; didn't read linux from scratch</a>
  <br/>
builing the kernel &mdash; <a href="https://github.com/comfies/tldrlfs/tree/master/init">installing an init</a> &gt;
</p>

---

The kernel source can be downloaded from many places, patched or otherwise, but one of the best places to get the source is [kernel.org](https://kernel.org).
If you're cloning a git repository, adding the depth flag with `--depth=1` will make the cloning process much quicker.

Regardless of your means of obtaining the source, extract as necessary and change directories.

```sh
$ export VER=5.13.12
$ wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-$VER.tar.xz
$ tar xf ./linux-$VER.tar.xz
$ cd ./linux-$VER
```

---

Configuration of the kernel can be done via `menuconfig`, `nconfig`, or `config`. The former two require ncurses to run.

```sh
$ make "$(nproc || printf '%s\n' 1)" mrproper
$ make "$(nproc || printf '%s\n' 1)" nconfig
```

If you wish to use the default configuration, using the `defconfig` make target will generate the default configuration.

```sh
$ make "$(nproc || printf '%s\n' 1)" defconfig
```

---

Building the kernel itself will take about four business days to complete, so you'll probably want to find something else to bide your time until compilation is complete. Unless you prefer to watch paint dry.

If you left module support enabled in the configuration you will need to execute the `modules_install` make target as well.

```sh
$ make "$(nproc || printf '%s\n' 1)"
# skip the next command if module support is disabled
$ make "$(nproc || printf '%s\n' 1" modules_install
```

---

Once compilation has completed, you'll copy the image to the boot directory of your installation. It is recommended that you also copy over the symbol file and configuration file, but not required.
While not required, it is also recommended that you prefix your kernel image filename with `vmlinuz-`.

```sh
$ mkdir $BUILD_DIR/boot
$ cp -iv arch/x86/boot/bzImage $BUILD_DIR/boot/vmlinuz-$VER
$ cp -iv System.map $BUILD_DIR/boot/System.map-$VER
$ cp -iv .config $BUILD_DIR/boot/config-$VER
```

---

<p align="center">
  <a href="https://github.com/comfies/tldrlfs/blob/master/CONTRIBUTING.md">tl;dr lfs needs help! feel free to contribute if you find something missing</a>
</p>
