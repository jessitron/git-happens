---
layout: illuminated
---

## Exercise: amend a commit

Make two commits.

    touch frogs
    git add frogs
    git commit -m "Amhpibians"

    touch crickets
    touch pillbugs
    git add --all .
    git commit -m "Insects"

Check the log.
Realize that you want to edit the commit message and a file two commits
back. How can you do this?

Here is one way to do it:

### Back up one commit.

    git reset HEAD@{1}

This says "Put head back where it was before my last operation." You
could also say

   git reset HEAD^

which says "Put head back at the first parent."
In either case, your git status should now show untracked files,
crickets and pillbugs.

Check the log and observe that the commit we want to amend (the
misspelled amphibians) is at the top. Add the file we want:

    touch lizards
    git add lizards

and now change the commit:

    git commit --amend

The editor opens, and you're free to correct the commit message.
Now don't forget to redo the insects commit that you backed out:

    git add crickets pillbugs
    git commit -m "insects"

### Another way to do it
Try doing something similar, only use

    git rebase -i HEAD^^

For the commit you want to alter, change the word "pick" to "edit" and
save the file. Follow instructions. Is it easier?
