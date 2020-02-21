# Installation

To install syslinux onto a given partition you will need a copy of it installed on the operating system in which TLDRLFS is being built from.

# Preparation

You will need to copy all .c32 files to a syslinux directory in the build directory.

```
cp /usr/lib/syslinux/bios/*.c32 /mnt/boot/syslinux/
```

You'll need to determine if the partition table is GPT or BIOS/MBR type.

```
blkid -s PTTYPE -o value /dev/sda
```

## GPT

```
sgdisk --attributes=1:set:2
dd bs=440 conv=notrunc count=1 if=/usr/lib/syslinux/bios/gptmbr.bin of=/dev/sdX
```

## MBR

```
dd bs=440 conv=notrunc count=1 if=/usr/lib/syslinux/bios/mbr.bin of=/dev/sdX
```

# Configuration

The most basic Syslinux configuration is just a label that is loaded. The configuration directory is `/boot/syslinux/syslinux.cfg`.

```
LABEL Linux
    LINUX ../vmlinuz-name
    APPEND root=/dev/sdXY loglevel=3 rw
```

# Installation

```
extlinux --install /mnt/boot/syslinux
```

If you get a message saying `/mnt/boot/syslinux is device /dev/sdb1` or something of the sort, do not fear, it still installed syslinux.
