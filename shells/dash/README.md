# Preparation
```
wget http://gondor.apana.org.au/~herbert/dash/files/dash-0.5.11.tar.gz
tar xf ./dash-0.5.11.tar.gz
cd ./dash-0.5.11
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
