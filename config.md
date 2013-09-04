---
layout: default
saying: Some people mistake it for a snack.
---

# Configuration

Where is it all?

First, don't bother looking at these files. Ask git to tell you what
your configuration is.

   git config -l

or, for a specific bit, if you know the exact key:

   git config --get core.autocrlf

When you want to set configuration, consider whether this is pertinent
to your current repository, to your user, or to everyone on your
computer. More specific levels will override broader levels.


## Repository-level

    git config --local -l

$GIT_CONFIG or .git/config

## User-level

    git config --global -l

~/.gitconfig

OR, if that doesn't exist and this other one does:

$XDG_CONFIG_HOME/git/config or ~/.config/git/config

## system level

    git config --system -l

<git installation>/etc/gitconfig

so, mine is at /usr/local/Cellar/git/1.8.3.4/etc/gitconfig


## Install git
Download and install git from [git-scm.org](http://git-scm.org/downloads)

You may already have it, as many packages include git these days. Type `git --version` at a command prompt to find out.

If you're on a Mac and have homebrew installed, then `brew install git`.

## GUI client

`gitk` comes with git. This will let you view your commit tree.

gitx is fantastic for Mac (and free) but is not yet compatible with git 1.8.

Tower is lovely for Mac, but not free.

The Github apps for Mac and Windows provide an easy-peasy interface to git, but they abstract a lot of the functionality. Therefore, we prefer command line.


## Github

Create a [github](http://github.com) user. This will let you copy everyone else's repositories.

## Github pages

If you're planning to make or modify a github-pages site like this one, and you have Ruby, then get jekyll. `gem install jekyll`





