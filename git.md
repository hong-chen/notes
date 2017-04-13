## __Git__

--------

remote server: __https://github.com__

username: __hong-chen__

name: __Hong Chen__

email: __me@hongchen.cz__

--------

__First time setup__

- __Mandatory__

```bash
git config --global user.name "Hong Chen"
git config --global user.email me@hongchen.cz
```

- __Optional__

```bash
git config --global core.editor vim
git config credential.helper 'cache --timeout=3600'
```

--------

__Basic commands__

- __Before changes are made__
```bash
git status # show current status
git branch # show current branch name

# create new branch named "develop-test1"
git branch develop-test1
# checkout to branch "develop-test1"
git checkout develop-test1

# create a new branch named "develop-test2" and checkout to it
git checkout -b develop-test2
```

- __After changes are made__

```bash
git checkout develop-test2
# ... after add a new file "README.md" ...
git add README.md
git commit -m "create README.md"
git pull origin develop-test2
git push -u origin develop-test2
```

--------

__How to initialize a local directory?__

e.g. `/Users/hchen/mygit/dotfiles`

```bash
cd /Users/hchen/mygit/dotfiles
git init
```
--------

__How to add a submodule?__

e.g. [reveal.js](https://github.com/hakimel/reveal.js/)

``` bash
git submodule add https://github.com/hakimel/reveal.js.git
git submodule update --init
```

--------
