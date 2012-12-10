---
layout: default
saying: Let's roll around in it together.
---

# Git Dojo: Plan

Git Dojo is one session where the more that goes wrong in the demo, the better. The following is a general plan, but when we go astray, great. The goal is to show what to do when you get off the happy path.

## Introduction
* github
* gh-pages
  * orphan branch
  * markdown
  * jekyll
    * if you have Ruby installed
    * `gem install jekyll`

## Setup
* download git: http://git-scm.com/downloads
* open your browser to http://jessitron.github.com/git-happens
* the repo for this site is at https://github.com/jessitron/git-happens
* we will add a few people as committers
  * add to the "Useful Pages" list in index.md the name of a page that they'd like to see covered
  * push your changes
* everyone else should [fork](fork.html) the repository and do what you like. You can
look for TODO or add to the list of pages you'd like to see
* clone your forked repository
* `git clone https://github.com/<YOUR_NAME>/git-happens.git`
* [configure git](commence.html)

## Make a commit
* add a new page to the list in index.md
* commit

## Oh crap, I should have done that on a branch
* `git branch addingNewPage`
* `git reset HEAD^`
* `git reset --hard`
* create the new page, change something else

## Oh crap, I meant to do that on the new branch
* `git stash save`
* `git checkout <NEW_BRANCH>`
* `git stash pop`
* commit

## Add a link to this new page in ... some page
* while we're in there, we see a TODO or a typo
* update the todo
* add the page
* save

## Oh crap, that small change should be in its own commit
* `git add -p`
* commit
* `git add`
* commit

## Make another change
* probably add something else to index.md
* commit

## fetch the latest
* `git fetch`
* make sure someone else has pushed
* checkout the main branch
* `git merge` (see that it does a fast-forward)

## rebase our branch in, interactively
* `git checkout newBranch`
* `git rebase -i gh-pages`
* put the small todo/typo fix at the beginning
* squash the new page into the one that added it to the index
* accidentally delete the other commit
* save and quit
* look at the result

## oh crap, I lost a commit!
* use `git reflog` to find the one we're missing
* `git cherry-pick <COMMIT_WE_WANT>`

## merge a pull request
* make sure it's one that will create conflicts

## try to push our changes
* oh crap, it won't go
* fetch again
* try to rebase. Notice conflicts. Get frustrated.
* `git rebase --abort`
* git rerere remembers merges so you never have to do the same one twice:
* `git config --global rerere.enabled true`

## merge our changes in
* set up the mergetool first
* use it to resolve conflicts
* complete the merge. Look at the tree.
* push


