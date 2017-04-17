## Shell (bash)

--------

### Customize (`~/.bash_profile`)

#### *Prompt*

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

### SSH login without password

Notes:

 - `username`: user name, e.g., `hchen`;
 - `remoteserver`: remote server, e.g., `skynet.colorado.edu`.

On local computer, type the following in a terminal

```bash
ssh-keygen -t rsa
```

for convenience, press `enter` two times.

On local computer, type the following in a terminal

<pre>
ssh <b>username</b>@<b>remoteserver</b> mkdir -p ~/.ssh
</pre>

and enter the password for the account on remote server.

On local computer, type the following in a terminal

<pre>
cat ~/.ssh/id_rsa.pub | ssh <b>username</b>@<b>remoteserver</b> 'cat >> ~/.ssh/authorized_keys'
</pre>

and enter the password for the account on remote server.

Now you can login in <code><b>username</b>@<b>remoteserver</b></code> without typing password.

--------

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

    `brew install homebrew/science/nccmp`

    `brew install open-mpi`

#### *Install libRadtran with GNU make*

<pre>
./configure --prefix=/Users/hchen/soft/libradtran/v2.0.1
make
make check
make install
</pre>

#### *Notes*

- If Anaconda is installed, remove it from `PATH` (simply comment out related lines in `.bash_profile`) before installation;

- Found a bug in `data/ic/yang2013/Makefile` and `data/ic/yang2013/Makefile.in`;

- After installation, add the following to `.bash_profile`,

  `export LIBRADTRAN_DATA_FILES="/Users/hchen/soft/libradtran/v2.0.1/share/libRadtran/data/"`
