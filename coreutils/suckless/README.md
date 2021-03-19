
```
git clone git://git.suckless.org/ubase
cd ubase
find . -name '*.c' -exec sed -i '1i #include <sys/sysmacros.h>' '{}' ';'
make "$(nproc || printf '%s\n' 1)"
make "$(nproc || printf '%s\n' 1)" PREFIX="$BUILDDIR/usr" install
cd ..
git clone git://git.suckless.org/sbase
cd sbase
make "$(nproc || printf '%s\n' 1)"
make "$(nproc || printf '%s\n' 1)" PREFIX="$BUILDDIR/usr" install
```
