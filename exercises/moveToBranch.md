---
layout: illuminated
---

## Setup

Here's a handy repository to clone:

    git clone https://github.com/jessitron/demoRepo
    cd demoRepo

You'll start out on the master branch.

### Make a few commits
Edit a file, add some changes, and commit. For instance:

    echo "This is fun -me" >> comments.txt

This adds the text to the file. You don't have to use that to make the
change, just do something. Check "git status" to see that a change was
noticed.

    git add comments.txt

This puts that change into the staging area. Check this with "git
status".

    git commit -m "Added my opinion to comments"

This creates a commit with the changes in the staging area. "-m"
supplies a commit messsage.

### Check the graph
Do this all the time! "git status" and "git log" are your friend. Use these
after every command to see where you are.
This command will show you a condensed version with information about
branches, drawing a cute little ascii commit graph:

    git log --oneline --graph --decorate

there should be some commits. Nothing too interesting.


## Exercise 1: "I wish I'd made this commit on a branch"

Oh no, a bug has occurred and it's time to postpone feature development.
But you just committed!
You need to get back to where the code was one commit ago and work on the
bug fix from there. If only you'd branched before you made this last
commit!

Here's your starting point: your master branch is one commit ahead of
origin/master:

    > git log --oneline --graph --decorate
    * 39f437b (HEAD, master) Added my opinion
    * 9f4f2bb (origin/master, origin/HEAD) Copied instructions here
    ...

Here's the goal: this latest commit is on a branch, and your master
branch pointer is back to the same commit as origin/master:

    > git log --oneline --graph --decorate branchypoo
    * 39f437b (branchypoo) Added my opinion
    * 9f4f2bb (HEAD, origin/master, origin/HEAD, master) Copied instructions here
    ...

go!

one answer:

### Step 1: create the feature branch you wish you had
We want to create a pointer, but we don't want to switch to that branch.

    git branch new-feature

New make sure your branch appears. Run git log with --decorate and see
your new branch name (along with the current branch and HEAD) at the top
commit.

### Step 2: move the current branch back one.
We want to rewind the current branch pointer, along with HEAD. Say "move
the current branch to the first parent of HEAD, and make all the files
in my working directory"

    git reset --hard HEAD^

--hard means "set my working directory too."
^ means "the first parent"

### Step 3: check your work
To see the whole result, check the decorated log of the new branch.
"decorate" means "Tell me where all branches and tags are."

    git log --oneline --decorate

Now look at the history of your current branch.

    git reflog

Do you see that two moves ago it pointed to the same place it does now?

## Variation A
"I made one commit and then did some more stuff and now
wish I'd branched"

If you hadn't committed all your work, some people would say, "stash
it!" I say "Commit it!" The branch is a storage place for unfinished
work. Go ahead and commit all the intermediate stuff, put a nice commit
message that tells you where you were, and proceed from above.

### How do I say "Go back two commits"?
In git, there are always several ways to specify a particular commit.
When in doubt, use "git show" to make sure you're finding the right one.
Try this:

    git show HEAD^^

if that's the last commit you want to keep, great.

## Variation B
"I want master to match what's on origin"

I do this a lot. Commit and branch to save current work, and then:

    git reset --hard origin/master

or more generally, to say "reset to the upstream of the current branch"

    git reset --hard @{u}

