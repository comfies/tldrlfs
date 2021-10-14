
```
wget https://ftp.gnu.org/gnu/coreutils/coreutils-8.32.tar.xz
tar xf ./coreutils-8.32.tar.xz
cd ./coreutils-8.32
CFLAGS="-static" ./configure --prefix=$BUILDDIR/usr
make -j$THREADS
make -j$THREADS install
```
