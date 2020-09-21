
```
wget https://www.busybox.net/downloads/busybox-1.31.1.tar.bz2
tar xf ./busybox-1.31.1.tar.bz2
cd ./coreutils-8.31
make defconfig
sed -i "s/\(^CONFIG_PREFIX=\).*/\1\"$(printf '%s\n' "$BUILDDIR/usr" | sed -e 's/[\/&]/\\&/g')\"/g" .config
make busybox
make install
```
