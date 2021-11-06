<p align="center">
  <a href="https://github.com">too long; didn't read linux from scratch</a>
  <br/>
&lt; <a href="https://github.com/comfies/tldrlfs/tree/master/shells">installing a shell</a> &mdash; installing a bootloader &mdash; <a href="https://github.com/comfies/tldrlfs/tree/master/bootloaders">core utilities</a> &gt;
</p>

---

For your BIOS or UEFI to determine which operating system to boot on a given device you may need to install a bootloader.

Back in the day, boot sectors on drives could not contain large files, nor could the execute many images directly. Thus the bootloader was born.

A bootloader is an image which would reside in the bootsector of your drive that could execute images stored in other parts of the drive, and often
would support a much larger variety of image types.

With the introduction of UEFI mostly came the primitivization of the bootloader. Bootloaders are no longer necessary to boot into different operating systems.

A user may still be inclined to use a bootloader, but know that with UEFI it is not at all necessary. See the EFISTUB section if you opt not to use a bootloader.

Do note that you will need a bootloader if you have a non-U/EFI system.

---

Installation guides

- [EFISTUB](#todo)
- [GRUB](#todo)
- [syslinux](https://github.com/Sweets/tldrlfs/tree/master/bootloaders/syslinux)

---

<p align="center">
  <a href="https://github.com/comfies/tldrlfs/blob/master/CONTRIBUTING.md">tl;dr lfs needs help! feel free to contribute if you find something missing</a>
</p>
