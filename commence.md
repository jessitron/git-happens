---
layout: default
saying: Don't fling it at your coworkers.
---
# Let's git to work

Download and install git from [git-scm.org](http://git-scm.org/downloads)

## Introduce yourself: Name, contact info, and favorite text editor

> Git keeps global configuration in .gitconfig in your home directory. Don't edit this file directly. Instead use the configuration commands in git. Show and modify configuration with `git config.` The `--global` makes the configuration apply to all your repositories. Without that, settings are local to the repo (and stored in `.git/.gitconfig`.)

1. Everybody must do these two things, or git will complain on every commit that it doesn't know who you are:

        git config --global user.name "John Doe"
        git config --global user.email johndoe@example.com

1. You'd best choose your editor and set it. Otherwise you'll probably be thrown into vi, and you might drown.

        git config --global core.editor textedit

    Change `textedit` to your editor of choice. The GIT_EDITOR environment variable, if set, will override this.  This editor is launched whenever git wants you to create or edit a commit message, or for an interactive rebase.

1. Git is more fun with colours.

        git config --global color.ui auto

## Choose your own adventure

Do you want to [create your own repo locally](init.html) or [copy someone else's repo](fork.html)?
