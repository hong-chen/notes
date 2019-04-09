### Install [libRadtran](http://www.libradtran.org) on Mac

#### *Download all the packages*
- [libradtran v2.0.1](http://www.libradtran.org/download/libRadtran-2.0.1.tar.gz)
- [optprop](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:optprop_v2.1.tar.gz)
- [ic_yang2013](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:ic_yang2013.tar.gz)
- [reptran](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:reptran_2015_all.tar.gz)

#### *Extract the downloaded packages to a existing directory (e.g. `~/soft/libradtran/v2.0.1_inst`)*

- libradtran v2.0.1

  `tar -xvzf libRadtran-2.0.1.tar.gz -C ~/soft/libradtran/v2.0.1_inst --strip-components=1`

- optprop

  `tar -xvzf optprop_v2.1.tar.gz -C ~/soft/libradtran/v2.0.1_inst/`

- ic_yang2013

  `tar -xvzf ic_yang2013.tar.gz -C ~/soft/libradtran/v2.0.1_inst/data/ic/yang2013/`

- reptran

  `tar -xvzf reptran_2015_all.tar.gz -C ~/soft/libradtran/v2.0.1_inst/`

#### *Check dependencies*

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

    `brew install open-mpi`

    `brew install https://raw.githubusercontent.com/Homebrew/homebrew-science/b9fd4d202e6f35cd4897962a05ad90d03d7c91f1/nccmp.rb`

The `nccmp` might not work but won't affect the libRadtran installation.


#### *Install libRadtran with GNU make*

<pre>
./configure --prefix=/Users/hchen/soft/libradtran/v2.0.1
make
make check
</pre>

#### *Notes*

- If Anaconda is installed, remove it from `PATH` (simply comment out related lines in `.bash_profile`) before installation;

- Found a bug in `data/ic/yang2013/Makefile` and `data/ic/yang2013/Makefile.in`;

- After installation, add the following to `.bash_profile`,

  `export LIBRADTRAN_DATA_FILES="/Users/hchen/soft/libradtran/v2.0.1/share/libRadtran/data/"`

- If your libRadtran configuration file cannot detect the required libraries even after you installed them, you can manually
specify the location through

  ```
  ./configure --prefix=/Users/hchen/soft/libradtran/v2.0.1
  --with-libnetcdf=/usr/local/Cellar/netcdf/4.4.1.1_6
  --with-libnetcdff=/usr/local/Cellar/netcdf/4.4.1.1_6
  LDFLAGS="-L/usr/local/Cellar/gmp/6.1.2/lib -L/usr/local/Cellar/gsl/2.4/lib"
  CPPFLAGS="-I/usr/local/Cellar/gmp/6.1.2/include -I/usr/local/Cellar/gsl/2.4/include"
  CXXFLAGS="-I/usr/local/Cellar/gmp/6.1.2/include -I/usr/local/Cellar/gsl/2.4/include"
  CFLAGS="-I/usr/local/Cellar/gmp/6.1.2/include -I/usr/local/Cellar/gsl/2.4/include"
  ```



---
 
