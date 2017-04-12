## __Git__

--------

remote server: __https://github.com__

username: __hong-chen__

name: Hong Chen

email: me@hongchen.cz

--------

__First time git setup__

- Mandatory

`git config --global user.name "Hong Chen"`

`git config --global user.email me@hongchen.cz`

- Optional

`git config --global core.editor vim`

`git config credential.helper 'cache --timeout=3600'`

--------

__How to initialize a local directory?__

e.g. `/Users/hchen/mygit/dotfiles`

`cd /Users/hchen/mygit/dotfiles`

`git init`

--------

__How to add a submodule?__

e.g. [reveal.js](https://github.com/hakimel/reveal.js/)

`git submodule add https://github.com/hakimel/reveal.js.git`

`git submodule update --init`

--------
