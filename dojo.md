---
layout: default
saying: Let's roll around in it together.
---

# Git Dojo: Plan

## Introduction. 
* github
* gh-pages
** branches (own initial commit, what's that called)
** site
* jekyll

## Setup
* add a few people as committers
** Tell them to make some changes and push: in particular, add to index.html the name of a page that they'd like to see added
** tell the others to fork and do what they like. They can look for TODO or add to the list of pages they'd like to see
* clone the repository

## Make a commit
* Add a new page to the list in index.md
* commit

## Oh crap, I should have done that on a branch
* git branch addingNewPage
* git reset HEAD^
* demonstrate git reset --hard
* create the new page

## Oh crap, I meant to do that on the new branch
* git stash save
* git checkout &lt;new branch&gt;
* git stash pop
* commit

## Add a link to this new page in ... some page
* While we're in there, we see a TODO or a typo
* update the todo.
* Add the page.
* save.

## Oh crap, that small change should be in its own commit
* git add -p
* commit
* git add
* commit

## Make another change
* probably add something else to index.md
* commit

## fetch the latest
* make sure someone else has pushed
* checkout the main branch
* merge-ff

## rebase our branch in, interactively
* Put the small todo/typo fix at the beginning
* squash the new page into the one that added it to the index
* accidentally delete the other commit
* look at the result

## oh crap, I lost a commit!
* use git reflog to find the one we're missing
* cherry-pick it in

## merge a pull request
* make sure it's one that will create conflicts

## try to push our changes
* oh crap, it won't go
* fetch again
* try to rebase. Notice conflicts, get frustrated
* mention git rerere
* rebase --abort

## merge our changes in
* set up the difftool first
* use it to resolve conflicts
* complete the merge. Look at the tree.
* push.


