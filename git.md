## __Git__

--------

remote server: __https://github.com__

username: __hong-chen__

name: __Hong Chen__

email: __me@hongchen.cz__

--------

__First time setup__

- __Mandatory__

<pre>
git config --global user.name "<b>Hong Chen</b>"
git config --global user.email <b>me@hongchen.cz</b>
</pre>

- __Optional__

<pre>
git config --global core.editor <b>vim</b>
git config credential.helper 'cache --timeout=<b>3600</b>'
</pre>

--------

__Create a repository__

- __Clone from existing repository on server__

<pre>
git clone <b>https://github.com/hong-chen/notes.git</b>
</pre>

- __Initialize local directory and link it to a repository server__

First go to the directory you want to initialize,

<pre>
cd <b>/Users/hchen/mygit/dotfiles</b>
</pre>

then,

<pre>
git init
</pre>

Then go to your git server, e.g., [github](https://github.com), and
create a emtpy new repository (no .gitignore, no README).

e.g., create a repository named `dotfiles` under account `hong-chen`.
There will be a link for the repository:

`https://github.com/hong-chen/dotfiles.git`.

Link your local directory to the newly created repository,

<pre>
git remote add origin <b>https://github.com/hong-chen/dotfiles.git</b>
</pre>
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
