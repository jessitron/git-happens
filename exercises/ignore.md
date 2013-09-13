---
layout: default
saying: If you close your eyes, you can still smell it.
---
# Ignoring files in git
Configuration controls which files in the working directory should not be stored in version control.This is called "gitignore" or "excludesfile."

## Why ignore files?
Some files don't belong in version control. Maybe they're big binaries that can be derived from the source already stored. Maybe they're IDE configuration files that are specific to your local environment.

## What to ignore?

Github has good examples of gitignore files for various kinds of projects. TODO: link

Ignore files that are personally yours. IDE configuration is an example. Personally, I name all my temp files "carrot."

* idea/
* .idea
* carrot

Ignore temporary files created by editors or operating systems. This will depend on your editor.

* \*~
* .\*.swp
* .DS_Store

Ignore files that are generated in the build.

* out/
* dist/
* \_site/ (for Jekyll projects like this one)

## How to ignore them?
Like most git configuration, you can tell it to ignore certain files either locally or globally. Either way, the technique is to create a file that holds the names of all files that shouldn't be stored in the repository. Here, "names" include wildcards, paths, etc. TODO: link to some external documentation with details

### ignore in this repository
What should be ignored locally? Anything that should be ignored by all users of this project. If everyone uses the same IDE, put IDE configuration files here. Files created by this project's build should be ignored at this level, too.

This is easy. Put the list of stuff to ignore in `.gitignore` in project root.

### ignore globally
This will ignore files in every repository you (as your user) use. I like to use this for my editor's temp files and irritating files my OS likes to create. Since global ignores are user-specific, these are files specific to me and my environment.

Two steps:

1. Create some file; mine in ~/.global_gitignore. Put the list of global excludes there.
2. Set this as your global gitignore.
        git config --global core.excludesfile &lt;filename&gt;

## Do you ignore .gitignore?
No, .gitignore should be commited to the repository. All copies of this repository should be ignoring roughly the same files. Otherwise, those files you want to ignore will be committed by someone else, and confusion ensues.

If there are some files you want to ignore but someone else might not, then put them in your global excludes; those are personal to you. Remember that the goal is to avoid surprise.


## I put the file in .gitignore but git status shows it as modified!

If you commit files and later decide to ignore them, you have to delete them from the repository. Git can't just forget about files it knows and loves.

    git rm -f <file or directory you want to ignore>    

> git rm says "Officially delete this file from the repository." For ignored files, this deletion is separate from whether the file still exists in your current directory. (todo: show git status) Comitting this will make the file untracked. Ideally, do this in the same commit as updating .gitignore.

    git commit -m "Deleting files that should be ignored"
