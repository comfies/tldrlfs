# Installation

To install syslinux onto a given partition you will need a copy of it installed on the operating system in which TLDRLFS is being built from.

# Preparation

You will need to copy all .c32 files to a syslinux directory in the build directory.

```
cp TODO: files
```

# Installation

```
extlinux --install /mnt/boot/syslinux
```

If you get a message saying `/mnt/boot/syslinux is device /dev/sdb1` or something of the sort, do not fear, it still installed syslinux.

TODO: shpeal about mbr and gpt and other bullshit
