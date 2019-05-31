# Source

```sh
git clone --depth=1 https://github.com/Sweets/hummingbird
cd ./hummingbird
```

---

# Preparing

```sh
mkdir -p $BUILDDIR/etc $BUILDDIR/sbin
install -Dm755 ./etc/rc.init $BUILDDIR/etc/rc.init
install -Dm755 ./etc/rc.shutdown $BUILDDIR/etc/rc.shutdown
```

---

# Building

```sh
DESTDIR=$BUILDDIR CC="gcc -static" make install
```

---

# Installation

```sh
cd $BUILDDIR
ln -s usr/bin/hummingbird sbin/init
```
