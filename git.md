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
git clone <b>https://github.com/hong-chen/dotfiles.git</b>
</pre>

<br><br>

- __Initialize local directory and link it to a server repository__

First go to the directory you want to initialize,

<pre>
cd <b>/Users/hchen/mygit/dotfiles</b>
</pre>

then,

<pre>
git init
</pre>

Then go to your git server, e.g., [github](https://github.com), and
create an emtpy new repository (no .gitignore, no README).

> Create a repository named `dotfiles` under account `hong-chen`.
> There will be a link for the repository:

`https://github.com/hong-chen/dotfiles.git`.

Link your local directory to the newly created repository,

<pre>
git remote add origin <b>https://github.com/hong-chen/dotfiles.git</b>
</pre>
--------

__Basic commands__

- __Before changes are made__

<pre>
git status
git branch

git branch <b>develop-test1</b>
git checkout <b>develop-test1</b>

git checkout -b <b>develop-test2</b>
</pre>

<br><br>

- __After changes are made__

<pre>
git checkout <b>develop-test2</b>
git add <b>README.md</b>
git commit -m "<b>create README.md</b>"
git pull origin <b>develop-test2</b>
git push -u origin <b>develop-test2</b>
</pre>

--------

__How to add a submodule?__

e.g. [reveal.js](https://github.com/hakimel/reveal.js/)

<pre>
git submodule add <b>https://github.com/hakimel/reveal.js.git</b>
git submodule update --init
</pre>
--------
