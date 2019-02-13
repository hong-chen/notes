### How to Compile with MPI

1. Change `FC = mpif90` and `FCFLAGS = -O3` in the file `Common.mk`;

2. Change `MPI_USE = 1` in the file `Makefile`.

Then compile the MCARaTS package through `make`.
