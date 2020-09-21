
```
git clone git://git.suckless.org/ubase
cd ubase
find . -name '*.c' -exec sed -i '1i #include <sys/sysmacros.h>' '{}' ';'
make
make PREFIX="$BUILDDIR/usr" install
cd ..
git clone git://git.suckless.org/sbase
cd sbase
make
make PREFIX="$BUILDDIR/usr" install
```
