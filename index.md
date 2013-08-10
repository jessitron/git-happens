---
layout: default
saying: Might as well run with it.
---

# Concepts

# Setup

# Reference

I promise in this talk that many sources on the Internet will tell you
what to type. Here are some of them.

<iframe src="http://player.vimeo.com/video/46010208" width="500" height="281" frameborder="0">do things right</iframe>
[Git Happens](http://vimeo.com/46010208) from [Saint Louis JavaScript Meetup](http://vimeo.com/stljs) on [Vimeo](https://vimeo.com).


The question that triggered my investigation of git was, "I wish I had
made this commit on a different branch. How do I move it?" The answer
is:

   git branch new-branch
This creates a pointer for the new branch, at the current commit.
Then when I have the old branch checked out, and git status is clean (no
unsaved changes in my working directory):

   git reset --hard HEAD^
This moves the current branch pointer back one. HEAD^ means "The parent
of the current HEAD commit" and --hard means "also make the files in the
working directory match the newly pointed-to commit"

At the end of this, my changes are on the new branch, and my repository
is set to the old branch, before that last commit.

Slides for Git Happens: [Git Happens
Prezi](http://prezi.com/xdvra221hg1n/git-happens/)

Follow me on twitter: [@jessitron](http://twitter.com/jessitron)
or read my blog: [Abstractivate](http://blog.jessitron.com)



