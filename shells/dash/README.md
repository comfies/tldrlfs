# Preparation
```
wget http://gondor.apana.org.au/~herbert/dash/files/dash-0.5.9.1.tar.gz
tar xf ./dash-0.5.9.1.tar.gz
cd dash-0.5.9.1
```

# Building
```
./configure --bindir=$BUILDDIR/usr/bin --mandir=$BUILDDIR/usr/share/man --enable-static
make
```

# Installation

```
make install
```
