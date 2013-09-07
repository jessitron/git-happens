---
layout: default
saying: Come out smelling like roses.
---

# Create your own repository

Git happens in a directory, and all files and subdirectories are (by default) saved in the repo.
if you haven't installed git yet, [please do](http://git-scm.com/downloads)

## Choose wisely

Go to what will be the root directory of your project. This becomes the *working directory* of your project.

> Please do not do this from your home directory, or from /, or from C:/. You will regret it. If you're playing around with git, create a directory and go there.

## Begin

    git init

This creates the .git directory. But it doesn't fully initialize the repository! Don't stop here! You must create your first commit. To do this you need to
* have at least one file
* add it to the staging area
* commit

## Reach out and

if your working directory doesn't have any files in it, create one.

    touch README.md

## Get on stage

Before you can commit anything, you have to stage it. This is like putting a piece of furniture on a pallet before shipping it out.

    git add README.md

> If you have other files in your working directory, you can include them all with `git add .`. But you might want to think about ignoring files before you add them all.

## That first commit

   git commit -m "Initial commit"

If the staging area is a pallet, then committing puts that pallet on the truck.

(If it complains about your username and email configuration, please
follow its instructions.)

Now your repository is properly initialized. Run gitk and check out your little commit tree. More of a commit seed, at this point: one little commit and a master branch pointer.

That's the minimum for creating a local repository. Let's put more thought into our repo, and [ignore some files](ignore.html)
