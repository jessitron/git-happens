-----
layout: illuminated
-----

## Commit date != author date
Make a commit with an author date that is different from its commit
date.

You can see both the author and commit dates with:

    git log --pretty=fuller

Here is one way to do it:
### create a branch
If you're on master, make an imaginary feature and check it out.

    git checkout -b branchypoo

### create the older commit
Make a commit on your branch. For instance:

    touch silly.txt
    git add .
    git commit -m "Silly file"

(Aside: "git commit -a" means "add all the changes before
committing" but it doesn't pick up untracked files. Untracked
files, boo!)

### create the newer commit
Switch back to your previous branch

    git checkout -

and make a commit there, with different changes.

You should now have different changes on two branches. Check this
with

    git log --oneline --graph --decorate master branchypoo

Notice that both branches are listed, so log will show both
branch-tips and everything in their histories. If you like,
substitute HEAD for the current branch's name.

### Rebase the branch
Rebase the older commit on top of the newer commit

    git checkout branchypoo
    git rebase master

### Check your work
Now observe the author and commit dates. Author date is when the code
was originally committed; commit date is when this commit
was added to the commit tree in its current location.

    git log --pretty=fuller


## Bonus
List the commits in order by author date.

Here is one way to do it:

    git log --pretty="%ai %h %s" | sort -r
