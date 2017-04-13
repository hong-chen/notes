## Shell (bash)

--------
<pre>
tar xvzf <b>some1.tar.gz</b> -C <b>/Users/hchen/Desktop/some2</b> --strip-components=1
</pre>
--------

### Install [libRadtran](http://www.libradtran.org) on Mac

First download all the packages:
- [libradtran v2.0.1](http://www.libradtran.org/download/libRadtran-2.0.1.tar.gz)
- [optprop](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:optprop_v2.1.tar.gz)
- [ic_yang2013](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:ic_yang2013.tar.gz)
- [reptran](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:reptran_2015_all.tar.gz)

Extract the downloaded packages to a directory (e.g. `~/soft/libradtran`):

- libradtran v2.0.1

  `tar -xvzf libRadtran-2.0.1.tar.gz -C ~/soft/libradtran/v2.0.1 --strip-components=1`

- optprop

  `tar -xvzf optprop_v2.1.tar.gz -C ~/soft/libradtran/v2.0.1/`

- ic_yang2013

  `tar -xvzf ic_yang2013.tar.gz -C ~/soft/libradtran/v2.0.1/data/ic/yang2013/`

- reptran

  `tar -xvzf reptran_2015_all.tar.gz -C ~/soft/libradtran/v2.0.1/`

<pre>
brew install gcc
brew install netcdf
brew install hdf5
brew install zlib
brew install gsl
brew install ndiff
brew install gawk
brew install homebrew/science/nccmp
brew install homebrew/science/petsc

make
make check
make install (a bug in data/ic/yang2013/Makefile is found)

export LIBRADTRAN_DATA_FILES="/Users/hoch4240/Chen/soft/libradtran/v2.0.1/share/libRadtran/data/"
</pre>
