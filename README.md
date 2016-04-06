# vim-fireplace-easy - A crackling Clojure fireplace 
This is a sample configuration for [vim-fireplace](https://github.com/tpope/vim-fireplace) to hopefully make the process of trying out Clojure with Vim straightforward. It is basically a complete Vim configuration with Fireplace for dynamic Clojure evaluation and [vim-clojure-static](https://github.com/guns/vim-clojure-static) for syntax highlighting etc.

## A quick note about Vim
Vim is an excellent and highly configurable text editor. You can extend Vim's capabilities using plugins - like Fireplace.

Vim reads configuration from two places: `~/.vim`, which holds plugins, and `~/.vimrc`, which stores your personal settings. This repository provides a version of both suitable for getting started with Clojure, though you may wish to add more settings and plugins.

## Install
If you have an existing Vim configuration, first move it out of the way. You can bring it back in after you feel like Fireplace is working for you.

    $ mv ~/.vim ~/.vim.bak
    $ mv ~/.vimrc ~/.vimrc.bak
    $ mv ~/.gvimrc ~/.gvimrc.bak

Now clone this repo into `~/.vim` and set it up:

    $ git clone git@github.com:ctford/vim-fireplace-easy.git ~/.vim
    $ ln -s ~/.vim/vimrc.vim ~/.vimrc
    $ vim -c "helptags ~/.vim/bundle/vim-fireplace/doc" -c "q"

The last command sets up helptags so that you can use `:help fireplace` to bring up Fireplace's documentation within Vim.

*Windows users see Windows Notes section below*

## First Test - Syntax Highlight and Stuff

Now open a Clojure file just to see if the plugin is working. Conveniently, there's one in this repo:

    $ vim ~/.vim/piglatin.clj

If syntax highlighting doesn't work, make sure `.vim` is in your home directory and `~/.vimrc` is a symlink to `~/.vim/vimrc.vim`.

## Starting nREPL 

Now we want to get to the serious stuff. Make sure you have [Leiningen](https://github.com/technomancy/leiningen) installed. Then, inside a Leiningen project:

    $ lein repl
    $ vim somefile.clj

Fireplace should automatically connect to the nREPL instance Leiningen has started for you.

## Second Test - The REPL

Start up Vim, open a Clojure file and run the `cqc` command. The Vim screen will split and you'll see a new Clojure REPL. Try it out.

## Third Test - Code

Place the cursor inside a Clojure expression and run the `cpp` command. Fireplace will evaluate the expression and display the result.

Place the cursor over a Clojure symbol and run the `K` command. Fireplace will display the documentation for that symbol.

Place the cursor over a Clojure symbol and run the `[d` command. Fireplace will display the source for that symbol.

# What's Next?

* Go read the Fireplace documentation! You can find it within Vim with `:help fireplace` or in `~/.vim/bundle/vim-fireplace/doc/fireplace.txt`.
* If you've already got Vim configuration, you should be able to copy this directory structure over yours. Then move the Pathogen and Fireplace settings from `vimrc.vim` to your `vimrc` file.
* Enable paredit.

# Paredit

Paredit performs structured editing of Clojure S-expressions. To enable, edit `vimrc.vim` and set the following:

    let g:paredit_mode = 1

The paredit documentation is here: `~/.vim/bundle/paredit-0.9.9/doc/paredit.txt`.

# ClojureScript

Fireplace doesn't have any particular support for ClojureScript, but you can at least enable syntax highlighting and stuff in `.cljs` files by adding this to your `vimrc` file:

    autocmd BufRead,BufNewFile *.cljs setlocal filetype=clojure

# Resources

* The [Vim Clojure google group](https://groups.google.com/group/vimclojure)
* Official [Fireplace repository](https://github.com/tpope/vim-fireplace)

# Thanks

* [Meikel Brandmeyer](https://github.com/kotarak), creator of the original [VimClojure](http://bitbucket.org/kotarak/vimclojure).
* [Dave Ray](https://github.com/daveray), who made [vimclojure-easy](https://github.com/daveray/vimclojure-easy).
* [Sung Pae](https://github.com/guns), who built [vim-clojure-static](https://github.com/guns/vim-clojure-static) from VimClojure.
* The indomitable [Tim Pope](https://github.com/tpope), author of [vim-fireplace](https://github.com/tpope/vim-fireplace) and many other useful Vim plugins.

# Windows Notes

Note if you're on Windows users:

* Replace `.vim` with `vimfiles`. The location of "HOME" may vary for you.
* Replace symlink `.vimrc` with `_vimrc` with contents `runtime vimrc.vim`. Or just move `vimrc.vim` to `_vimrc`.
