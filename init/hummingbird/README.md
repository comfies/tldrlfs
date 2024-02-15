# Source

```sh
git clone --depth=1 https://github.com/Sweets/hummingbird
cd ./hummingbird
```

---

# Preparing

```sh
mkdir -p $BUILDDIR/usr/lib/hummingbird $BUILDDIR/sbin
make -j$THREADS DESTDIR=$BUILDDIR install
```

---

# Building

```sh
DESTDIR=$BUILDDIR CC="gcc -static" make install
```

---

# Installation

```sh
install -Dm755 usr/lib/hummingbird/fs "$BUILDDIR/usr/lib/hummingbird/fs"
install -Dm755 usr/lib/hummingbird/tty "$BUILDDIR/usr/lib/hummingbird/tty"
cd $BUILDDIR
ln -s usr/bin/hummingbird sbin/init
```
