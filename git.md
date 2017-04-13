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
git config --global user.name "___Hong Chen___"
git config --global user.email ___me@hongchen.cz___
```

- __Optional__

```bash
git config --global core.editor ___vim___
git config credential.helper 'cache --timeout=___3600___'
```

--------

__Create a repository__

- __Clone from existing repository on server__

```bash
git clone ___https://github.com/hong-chen/notes.git___
```

- __Initialize local directory and link it to a repository server__

First go to the directory you want to initialize,

```bash
cd /Users/hchen/mygit/dotfiles
```

then,

```bash
git init
```

Then go to your git server, e.g., [github](https://github.com), and
create a emtpy new repository (no .gitignore, no README).

e.g., create a repository named "dotfiles" under account "hong-chen".
There will be a link for the repository:

`https://github.com/hong-chen/dotfiles.git`.

Link your local directory to the newly created repository,

```bash
git remote add origin https://github.com/hong-chen/dotfiles.git
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

__How to add a submodule?__

e.g. [reveal.js](https://github.com/hakimel/reveal.js/)

``` bash
git submodule add https://github.com/hakimel/reveal.js.git
git submodule update --init
```
--------
