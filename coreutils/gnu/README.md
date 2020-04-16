
```
wget https://ftp.gnu.org/gnu/coreutils/coreutils-8.31.tar.xz
tar xf ./coreutils-8.31.tar.xz
cd ./coreutils-8.31
CFLAGS="-static" ./configure --prefix=$BUILDDIR/usr
make
make install
```
