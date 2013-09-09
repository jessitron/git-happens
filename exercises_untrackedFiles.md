---
layout: illuminated
---

## Exploring untracked files

If you want to follow along...

Clone [this repository](https://github.com/jessitron/demoRepo):

    git clone https://github.com/jessitron/demoRepo.git

## Sneaky evil overwriting

    git checkout untrackedFiles/a

create a useful temp file:

    echo "Don't lose this" >> temp.txt

Notice that git status shows no changes. why?

now switch branches:
    git checkout untrackedFiles/b

What is in temp.txt now?

now switch back:
    git checkout untrackedFiles/a

where is your temp file???

The lesson here is: Keep .gitignore the same between branches. Establish
what belongs there early and stick with it.
And, when you add something to .gitignore, also remove it from the
repository using "git rm" (preferably in the same commit that you add
it to .gitignore).

## appearing files

move to branch a

    git checkout untrackedFiles/a

now create a file called temp.md

    touch temp.md

Observe that git status is clean, no changes. now switch back to b

    git checkout untrackedFiles/b

git status, and observe that is shows an untracked file. How annoying!
Again, .gitignore is different between branches, and that's bad.

Get rid of all untracked files and directories with:

    git clean -df
