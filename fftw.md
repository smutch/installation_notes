# FFTW

Meraxes requires FFTW3 built with ceratin flags.  This can be achieved with the following:

```
./configure --prefix=[YOUR PREFIX HERE] CFLAGS=-fPIC --enable-shared --enable-float --enable-mpi
make -j 4
make install
```
