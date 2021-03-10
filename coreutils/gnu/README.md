
```
wget https://ftp.gnu.org/gnu/coreutils/coreutils-8.32.tar.xz
tar xf ./coreutils-8.32.tar.xz
cd ./coreutils-8.32
CFLAGS="-static" ./configure --prefix=$BUILDDIR/usr
make "$(nproc || printf '%s\n' 1)"
make "$(nproc || printf '%s\n' 1)" install
```
