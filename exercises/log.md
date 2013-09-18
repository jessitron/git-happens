---
layout: illuminated
---

## Exercise: dig through history

### Setup
clone https://github.com/jessitron/scalacheck.git

### Q1: Who affected this code?
Say we're interested in BigDecimals. We want to know
the history of the ScalaCheck Generator for BigDecimals.

#### Q1A: Search commit messages

Grep the commit messages, displaying all the ones that contain
BigDecimal.

one answer:

    git log --grep="BigDecimal"

#### Q1B (optional): Search diffs

Find all commits that have BigDecimal in their changes.

one answer:

    git log -G'BigDecimal' -p --word-diff=color

This should display four commits, and some changes in each one.

-G&lt;regex&gt; means "show only commits with this phrase in the diff"

-p means "show the patch that represents the changes in this commit"

--word-diff=color says "show the words that changed in red and
green"

Another useful option is -S instead of -G, which says, "show only
commits that added or deleted the phrase; I don't care if it moved
around."

#### Q1C (optional): Search within all the code, at any commit

Choose one of the commits that came up in that log. Grep the codebase as
of that commit for BigDecimal.

one answer:

    git grep -p -C3 BigDecimal e19204e

This shows all occurrences of BigDecimal in the code as of commit
e19204e.

-p says "Try to display the function name each mention is in." It
doesn't work very well in Scala.

-C3 says "Show three lines of context on either side of the occurrence."

BigDecimal is the expression. It could be a regex.

e19204e is a commit hash. If you leave this off, git will look in the
current working directory.

other useful options:
* --whole-function, which tries to display the whole function context. In Scala, that winds up being most of the file.
* -h, don't show the filename
* -n, show line numbers

### Q2: Zooming in on context

#### Q2A: Ancient history.
List all commits since May 31st, 2011.

one answer:

    git log --before='May 31 2011'

a caution with "before" and "since": They select on author date, not
commit date.

Commits are ordered by author date in the log unless --graph is given.

#### Q2B: See the parents

Hey, there's that merge commit about BigDecimal, third one down! Its
hash starts with ea63787ea

Let's look more closely. Graph its history. Display the author.

Notice that this commit merged a branch, without any changes happening
on master while the branch was in progress. On a local branch, this
could have been a fast-forward merge. Pull requests create a merge
commit like this, and you can choose this too, with git merge --no-ff.

one answer:

    git log --graph --format=short ea63787ea


#### Q2C: Follow the first parents down

Print the log for only the first parent of this commit. You should see
commit e0cb3ba73. Then print the first parent of that commit - it
should be af28cf6d1 "Fixed issue #86".

one answer:

    git log -1 ea63787ea~
    git log -1 ea63787ea~~

-1 means "stop after one commit." Other numbers work too.

Now try using ~2 instead of ~~. Is it the same?

~ always follows the first parent.

#### Q2D: Follow the second parent down.

Print the log for the second parent of ea63787ea.

one answer:

    git log ea63787ea^2

Try changing ^2 to ^^. Does it do the same thing?

^ follows the parent you specify with a number, defaulting to 1.

### Q3: Range selection

Now for the hard one. List all commits that are on the branch merged in
by ea63787ea, and none of the commits before the branch.

You should see two commits, one with the fix and one with the failing
test.

one answer:

    git log ea63787ea^..ea63787ea^2

this says "all the commits on the second parent that aren't in the
history of the first."

Another useful option is --reverse, so you can read down in
chronological order.

### Q4: See the whole file

Display the entire contents of the one file that is contained in the
"Test that shows failing BigDecimal generation" commit.

one answer:

Find out what files changed:

    git show --name-only ea63787ea^2^

--name-only displays only files that changes.

This shows information about the first parent of the second parent of
ea63787ea. (Read the commit address backwards.)

Display the contents of that file:

    git show e19204e093:src/test/scala/org/scalacheck/GenSpecification.scala

git show is a useful way to display whatever's in a file, at any commit.







