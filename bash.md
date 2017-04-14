## Shell (bash)

--------

### Customize (`~/.bash_profile`)

#### _Prompt_

- [bash-git-prompt](https://github.com/magicmonty/bash-git-prompt)

  Add the following to `~/.bash_profile`,

  ```bash
  if [ -f "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh" ]; then
      GIT_PROMPT_START="\e[0;32m\u\e[0m at \e[0;31m$(scutil --get ComputerName)\e[0m in \e[0;34m\$PWD/\e[0m"
      GIT_PROMPT_END="\n->"
      __GIT_PROMPT_DIR=$(brew --prefix)/opt/bash-git-prompt/share
      source "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh"
  fi
  ```

--------

### Install [libRadtran](http://www.libradtran.org) on Mac

#### _Download all the packages_
- [libradtran v2.0.1](http://www.libradtran.org/download/libRadtran-2.0.1.tar.gz)
- [optprop](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:optprop_v2.1.tar.gz)
- [ic_yang2013](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:ic_yang2013.tar.gz)
- [reptran](http://www.meteo.physik.uni-muenchen.de/~libradtran/lib/exe/fetch.php?media=download:reptran_2015_all.tar.gz)

#### _Extract the downloaded packages to a directory (e.g. `~/soft/libradtran/v2.0.1_inst`)_

- libradtran v2.0.1

  `tar -xvzf libRadtran-2.0.1.tar.gz -C ~/soft/libradtran/v2.0.1_inst --strip-components=1`

- optprop

  `tar -xvzf optprop_v2.1.tar.gz -C ~/soft/libradtran/v2.0.1_inst/`

- ic_yang2013

  `tar -xvzf ic_yang2013.tar.gz -C ~/soft/libradtran/v2.0.1_inst/data/ic/yang2013/`

- reptran

  `tar -xvzf reptran_2015_all.tar.gz -C ~/soft/libradtran/v2.0.1_inst/`

#### _Check dependencies_

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

#### _Install libRadtran with GNU make_

<pre>
./configure --prefix=/Users/hchen/soft/libradtran/v2.0.1
make
make check
make install
</pre>

#### _Notes_

- If Anaconda is installed, remove it from `PATH` (simply comment out related lines in `.bash_profile`) before installation;

- Found a bug in `data/ic/yang2013/Makefile` and `data/ic/yang2013/Makefile.in`;

- After installation, add the following to `.bash_profile`,

  `export LIBRADTRAN_DATA_FILES="/Users/hchen/soft/libradtran/v2.0.1/share/libRadtran/data/"`
