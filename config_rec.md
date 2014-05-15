-----
layout: default
saying: and we're all happening too
-----

## Recommended configuration

a record of configuration parameters that I set


### Editor

by default, the editor is vi. There are other ways to set it, but I
recommend choosing yours in the global config.

On Windows:

    git config --global core.editor notepad

On Mac, textedit is nonthreatening, or change it to your favorite
editor.

    git config --global core.editor textedit

If you like vi but have a spiffy setup that sometimes changes the return
values, git will do weird things like reject your commit messages. In
that case, set the explicit path to vim.

    git config --global core.editor /usr/bin/vim

### Default merge behavior

I like to type "git merge" when I'm on master, and have it merge
origin/master by default.

    git config --global merge.defaulttoupstream true

### Push behavior

When I say "git push" I want only my current branch to go.

    Git 1.8: git config --global push.default simple

    older Git: git config --global push.default current


### Other

    git config --global core.excludesfile $HOME/.gitignore
    git config --global color.ui true
