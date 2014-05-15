---
layout: default
saying: Don't fling it at your coworkers.
---
# Configure git

Git configuration comes in three categories: personal preference, good idea, and essential for life.

## Introduce yourself: Name, contact info, and favorite text editor
This is essential for life.

> Git keeps global configuration in .gitconfig in your home directory. Don't edit this file directly. Instead use the configuration commands in git. Show and modify configuration with `git config.` The `--global` makes the configuration apply to all your repositories. Without that, settings are local to the repo (and stored in `.git/.gitconfig`.)

1. Everybody must do these two things, or git will complain on every commit that it doesn't know who you are:

        git config --global user.name "John Doe"
        git config --global user.email johndoe@example.com

1. You'd best choose your editor and set it. Otherwise you might be thrown into vi, and that's just cruel.

        git config --global core.editor textedit

    Change `textedit` to your editor of choice. The GIT_EDITOR environment variable, if set, will override this.
> This editor is launched whenever git wants you to create or edit a commit message, or for an interactive rebase. That is, pretty much all day. If you don't have a usable editor configured here, then you can't make a commit unless you supply the commit message with -m.

## Good Ideas
1. Git is more fun with colours.

        git config --global color.ui auto

1. Default to "do things right" when merging. This says "When I say 'git
merge' then merge to the code I am trying to keep in sync with"

        git config --global merge.defaulttoupstream true

1. Default to "do things right" when pushing. This says "When I say 'git
push' then push the branch I'm on, and nothing else"

        git config --global push.default simple

## Personal Preference

If you have an editor that creates temp files, or maybe a Mac with its
infernal .DS_Store, you can list those in a file somewhere and then tell
git to read that file and exclude everything you listed.

    git config --clobal core.excludesfile $HOME/.gitexcludes
