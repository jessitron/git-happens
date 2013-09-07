---
layout: default
saying: Some people mistake it for a snack.
---

# Configuration

Where is it all?

This documents where configuration files are located, but don't bother
looking at them. Ask git to tell you what
your configuration is:

   git config -l

or, for a specific bit, if you know the exact key:

   git config --get core.autocrlf

When you want to set configuration, consider whether this is pertinent
to your current repository, to your user, or to everyone on your
computer. More specific levels will override broader levels.


## Repository-level

    git config --local -l

This goes in a file at $GIT_CONFIG or .git/config

## User-level

    git config --global -l

This goes into ~/.gitconfig

OR, if that doesn't exist and this other one does, it'll go to
$XDG_CONFIG_HOME/git/config, where XDG_CONFIG_HOME defaults to
~/.config.

## system level

    git config --system -l

This lives in etc/gitconfig in the git installation directory.
 For instance, I used brew to install git, so mine is at /usr/local/Cellar/git/1.8.3.4/etc/gitconfig

## Install git
Download and install git from [git-scm.org](http://git-scm.org/downloads)

You may already have it, as many packages include git these days. Type `git --version` at a command prompt to find out.

If you're on a Mac and have homebrew installed, then `brew install git`.





