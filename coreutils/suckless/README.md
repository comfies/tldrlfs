
```
git clone git://git.suckless.org/ubase
cd ubase
find . -name '*.c' -exec sed -i '1i #include <sys/sysmacros.h>' '{}' ';'
make -j$THREADS
make -j$THREADS PREFIX="$BUILDDIR/usr" install
cd ..
git clone git://git.suckless.org/sbase
cd sbase
make -j$THREADS
make -j$THREADS PREFIX="$BUILDDIR/usr" install
```
