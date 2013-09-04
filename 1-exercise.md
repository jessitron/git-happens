---
layout: default
saying: You can be happening too
---

# Setup
## Create a local repository
If you don't know how, check [these instructions](init.html)

## Make a few commits
Edit a file, add your changes, and commit.
End with a commit message like "Halfway through a sticky feature"

## Check the graph

    git log --oneline --graph --decorate

there should be some commits. Nothing too interesting.

# Exercise 1: "I wish I'd made this commit on a branch"

Oh no, a bug has occurred and it's time to postpone feature development.
But you just committed!
You need to get back to where the code was one commit ago and work on the
bug fix from there. If only you'd branched before you made this last
commit!

Here's how to do it:

## Step 1: create the feature branch you wish you had
We want to create a pointer, but we don't want to switch to that branch.
    git branch new-feature

New make sure your branch appears. Run git log with --decorate and see
your new branch name (along with the current branch and HEAD) at the top
commit.

## Step 2: move the current branch back one.
We want to rewind the current branch pointer, along with HEAD. Say "move
the current branch to the first parent of HEAD, and make all the files
in my working directory"

    git reset --hard HEAD^

--hard means "set my working directory too."
^ means "the first parent"

## Step 3: check your work
To see the whole result, check the decorated log of the new branch:

   git log --oneline --decorate

## Variation: "I made one commit and then did some more stuff and now
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

## Advanced variation: "I want master to match what's on origin"
(no, we haven't covered this, but a lot of you probably have this
question)
I do this a lot. Branch to save current work, and then:

    git reset --hard origin/master

or more generally, to say "reset to the upstream up the current branch"

    git reset --hard @{u}

