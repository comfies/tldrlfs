
```
wget https://www.busybox.net/downloads/busybox-1.33.0.tar.bz2
tar xf ./busybox-1.33.0.tar.bz2
cd ./busybox-1.33.0
make -j$THREADS defconfig
sed -i "s/\(^CONFIG_PREFIX=\).*/\1\"$(printf '%s\n' "$BUILDDIR/usr" | sed -e 's/[\/&]/\\&/g')\"/g" .config
make -j$THREADS busybox
make -j$THREADS install
```
