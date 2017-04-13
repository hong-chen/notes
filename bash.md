## Shell (bash)

### Install [libRadtran](http://www.libradtran.org) on Mac

#### Download all the packages
- [libradtran v2.0.1](http://www.libradtran.org/download/libRadtran-2.0.1.tar.gz)
- [optprop](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:optprop_v2.1.tar.gz)
- [ic_yang2013](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:ic_yang2013.tar.gz)
- [reptran](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:reptran_2015_all.tar.gz)

#### Extract the downloaded packages to a directory (e.g. `~/soft/libradtran`)

- libradtran v2.0.1

  `tar -xvzf libRadtran-2.0.1.tar.gz -C ~/soft/libradtran/v2.0.1_inst --strip-components=1`

- optprop

  `tar -xvzf optprop_v2.1.tar.gz -C ~/soft/libradtran/v2.0.1_inst/`

- ic_yang2013

  `tar -xvzf ic_yang2013.tar.gz -C ~/soft/libradtran/v2.0.1_inst/data/ic/yang2013/`

- reptran

  `tar -xvzf reptran_2015_all.tar.gz -C ~/soft/libradtran/v2.0.1_inst/`

#### Check dependencies

- Xcode

  Download Xcode from App Store and install command line tools (simply open Xcode).

- gcc and gfortran

  try:

  `which gcc`

  `which gfortran`

  If nothing returns, install gcc through [homebrew](https://brew.sh/), e.g.,

  `brew install gcc`

- other libraries

    `brew install hdf5`

    `brew install zlib`

    `brew install netcdf`

    `brew install gsl`

    `brew install ndiff`

    `brew install gawk`

    `brew install homebrew/science/nccmp`

    `brew install open-mpi`

#### Install libRadtran with GNU make
<pre>
./configure --prefix=/Users/hchen/soft/libradtran/v2.0.1
make
make check
make install
</pre>

#### Notes

- If Anaconda is installed, remove it from `PATH` (simply comment out related lines in `.bash_profile`) before installation;

- Found a bug in `data/ic/yang2013/Makefile` and `data/ic/yang2013/Makefile.in`;

- After installation, add following to `.bash_profile`,

  `export LIBRADTRAN_DATA_FILES="/Users/hchen/soft/libradtran/v2.0.1/share/libRadtran/data/"`
