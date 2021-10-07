<p align="center">
  <a href="https://github.com">too long; didn't read linux from scratch</a>
  <br/>
&lt; <a href="">builing the kernel</a> &mdash; installing an init &mdash; <a href="">installing a shell</a> &gt;
</p>

---

The kernel does not boot into a usable system on its own. The kernel will execute the path defined in the `init` kernel parameter whenever it is ready to drop the user from kernel space. If the kernel parameter is not provided, the kernel will attempt to execute any of `/sbin/init`, `/etc/init`, `/bin/init`, whichever is found first.

If no working init is found, the kernel will attempt to execute the binary at path `/bin/sh`. If all else fails, a kernel panic will ensue.

---

There is no real requirement for what process is executed as PID 1. If you have embedded hardware that only ever runs one program, it may be in your best interest to just point the `init` path to that program. On a desktop, however, typically there is a program that will spawn more processes to make the system more usable to the end user.

These programs are called "inits." In some cases they may be complex systems which interface with the child processes, and in others they may be simple programs that attempt to spawn children but have no regard for whether they succeed, fail, or even die at a later point in time.

---

Installation guides

- [hummingbird](https://github.com/comfies/tldrlfs/tree/master/init/hummingbird)

---

<p align="center">
  <a href="https://github.com/comfies/tldrlfs/blob/master/CONTRIBUTING.md">tl;dr lfs needs help! feel free to contribute if you find something missing</a>
</p>
