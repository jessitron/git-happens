---
layout: default
saying: Try it, try it, Sam I Am!
---

# Git for Scientists

This is created for Software Carpentry's WISE bootcamp, 14 Apr 14.

[Software Carpentry's
lessons](http://swcarpentry.github.io/2014-04-14-wise/novice/git/)
are a good intro if you want to read ahead.

## What is git?

Git is a version control system. It's the current top-of-the-line one,
used by programmers and conscientious people everywhere.

## What is version control?

Version control tracks changes in files over time. It keeps the
progression of a project, trackably, without cluttering the filesystem.

Version control is like saved games. Use it to mark any point you might
want to come back to. Use it to see what changed, when.

In addition, version control coordinates changes to the same files by
many people. Use it to collaborate without overwriting team members'
work.

## Why do I care?

Version control is essential for reproducibility of results. You can get
back to any version of your code. You can see who changed what, and
when, and (with good practice) why. You can give other people access to
see or change your files without fear that they'll overwrite anything
you needed.

That's the excuse, the external reason to use git. The day-to-day reason
is: it provides safety and lets us experiment. Save something, make
changes, and always know you can change your mind. Track what you did.

Other benefits:

 * easy and fast backups.
 * everyone can work at the same time, on separate computers, with no locking.

## What's the downside?

Long-term, the downside is a bit of extra work, a few extra commands to
type a few times per day. There's some extra brainspace required there.

Setup is easier than any other version control system. You do need to
decide whether to backup or share your repository.
You'll also want to figure out the git integration in your favorite
development tools.

Short-term, learning git is tough. The concepts in it are new, but
interesting. The commands to do things are new, and not as easy as I
wish they could be. But that's why you're here!

# Today

We have all afternoon to learn this. The goal is, before you leave today
you know how to use git locally to save multiple versions of files, and
to collaborate with a central repository at Bitbucket or Github.

We'll start with the concepts behind git and how it organizes the
versions of files internally. Then we'll create a local repository, save
some changes, and get back to old versions. After the break, we'll
backup our repository to Bitbucket, and then learn how to collaborate
with each other.

## Concepts

Before typing anything, let's get an idea of how git thinks about your
files.

A project is a directory, including all subdirectories and all the files
on down. By default, git saves the contents of everything under the
project root directory when you save your game.

A repository is "a storage location, often for safety or preservation."
In the case of git, it's a compressed and carefully organized copy of
all your saved games. This always lives inside a sneaky subdirectory
(called .git) in the project root. Copies of it can also live elsewhere,
such as Bitbucket, Github, and collaborators' computers.

A commit is a saved game. Every commit includes:

* a full snapshot of all the files in your project
* a message, where you can describe why changes were made
* a record of who saved it and when
* a reference to the prior commit, so you can see what changed.

Each commit encapsulates a set of changes. These saved games are always
available to restore, to compare with, and to share with others (if you
choose to publish them).

## Get Started

Git commands start with `git` and then what you want to do. The first
ones to learn are `config`, `status`, `add`, `commit`, and `log`. A few
uses of each of these, and we can create saved games and review our
progression.

### One-time setup

After installing git, there are a few one-time configuration commands that tell
git who you are. Please replace the name and email with yours, and the
editor "nano" with whatever is your favorite.

    git config --global user.name "Vlad Dracula"
    git config --global user.email "vlad@tran.sylvan.ia"
    git config --global color.ui "auto"
    git config --global core.editor "nano"

### Your First Repo

Execute these commands in the terminal on a Mac, or in Git Bash on
Windows.

1. Make a directory, a whole new directory, to be the project root.

    mkdir poetry

2. Go into that directory. Most git commands are best executed when
you're at project root.

    cd poetry

3. Create a file in that directory, representing the initial version of
your work or program. (I'm going to construct a poem.)

    nano poem.txt
    (insert text "The old crow is getting slow")
    (save and quit)

4. List the files in the directory. you should see only poem.txt

Now, say, I'm getting ready to change my poem. And I think, "Oh, I
should save this first, so I can change my mind later. And tell when I
changed it, and why." The save button in your editor writes it to a file
that can change. Version control preserves it forever, like a museum,
with little signs in front of it explaining it to users.

<a
href="http://www.tripadvisor.com/LocationPhotoDirectLink-g32655-d103412-i90615363-Natural_History_Museum_of_Los_Angeles_County-Los_Angeles_California.html#90615363"><img
alt=""
src="http://media-cdn.tripadvisor.com/media/photo-s/05/66/ae/43/natural-history-museum.jpg"/></a><br/>This
photo of Natural History Museum of Los Angeles County is courtesy of
TripAdvisor

5. Create a git repository to preserve stuff in this directory.

    git init

6. Check the status. I type `git status` about every other command. Also
check `ls -a`, and see the new `.git` directory. You never need to use
that, but feel reassured that museum specimens are stored there.
7. "Untracked files" is a bad thing. Tell git that yes, we want it to
babysit this file, and we're about to save it.

   git add poem.txt

8. Check the status. Git now has this file, in its current state, on its
preservation station, ready for carbon freeze.
9. Save the game! When you type this, git is going to open your editor.
that's where you'll fill in the sign, explain the purpose of these
changes.

   git commit
   (type a commit message, save and commit)

10. Check the status. It is all clear.
11. Now it's finally time to make that change. Edit the file and add a
line.
12. Check the status. (every even numbered step!) Git notices the
changes. They're not yet in the preservation station.
13. Here's a shortcut, when all you have is changes to existing file, to
make a commit quickly. The `-a` option to `commit` means "include all
outstanding changes to existing files." The `-m` option means "Here
comes a commit message right here."

    git commit -am "Added line 2 to poem"

14. Check the status. All clear.
15. Now pretend it's a week later, and we come back and ask, what was I
doing in this project anyway? It's time to take a peek at our exhibit so
far. When we ask git for the log, it shows up. By default it opens the
log inside `less`, which is a program for viewing files longer than the
screen. This won't make a difference when our log is so short. Later on,
you can hit `q` to exit without scrolling through the whole log.

    git log

If these are the only commands you know, this is sufficient to preserve
the history of your project, and retain reproducibility. `git add` new
files, and then `git commit` at least daily with a useful message.

## Using your saved games

All this historical context is useful to see what's changed, and to move
to a previous state.

1. Identify a saved game by its commit name
2. Show the changes that happened in that commit

    git log -p <commit>

3. Show the difference between that commit and the last commit

   git diff <commit>..HEAD

4. Go back to that saved game.

   git checkout <commit>

5. Check the status. What is this detached HEAD state?? It says, if
you're going to save any new games from this point, you need to name
your alternate history. Now it's time to talk about how git records
history, how it keeps context: the commit graph.

## More saved-game slots
Or, alternate histories in the museum.

1. Pointers into the graph: branches
2. The current-place bookmark: HEAD
3. See how the branches relate

   git log --graph --oneline --decorate --all

4. Switching branches
5. Bringing changes into master with fast-forward
6. Tags give a commit a permanent name

## Local: Conclusion
With this, you can track your own project's progress. You can label
versions with tags, justify changes in commit messages, and reproduce
the state of your project at any point. You can experiment, save these
changes to another saved game, and bring them into the mainline when you
choose. All this makes the process of development and writing more
legible and measurable. And when it's legible, we can scale it up! Next
is to add offsite backup, and then collaborators.

# Remote

## Offsite backup
Note: everywhere you see "bitbucket" or "Github" you may substitute one
for the other.

The quickest win of replicating your repository to other locations is
for your own use. You have an extra copy of every version of your
project ever, in the cloud or on a server. You can update this when you
wish. The next quickest win is: collaborating with yourself, on another
computer. You can have completely separate copies, and yet keep them up
to date with each other as you choose.

This is different from Dropbox. Git doesn't do anything you don't tell
it to do. This may seem like extra work when you're collaborating with
yourself, but it's essential when you collaborate with other people.

1. Create an account at bitbucket
2. Create a new repository on bitbucket
3. Add bitbucket as a remote.
4. Push the contents of your repository up.

   git push -u <bitbucket url>

5. See your work on bitbucket.
6. In the terminal, edit the poem.txt again. Add another line.
7. `git add` and `git commit` the change.
8. Check the status. See that it tells you, you are one commit ahead of
origin. That means you have changes locally that you haven't shared yet.
9. `git push` to update the remote repository with your changes.
10. See that the repository in bitbucket has the new commit.

At this point, you can use the bitbucket repository to collaborate with
yourself: access it, and get and push changes from multiple computers.

## Collaboration

Time to work together!
1. Pair up with a person next to you. (Three in a group is OK too.)
Choose one person's repository to collaborate on.
2. The repository owner: give update permissions to the other person or people.
3. Everyone else: clone the shared repository.

    git clone <bitbucket url>

8. Check the status and the log. Everyone should see the same stuff.
9. One person, create a file name.txt.
10. `add` and `commit` it, then `git push` to share it.
11. Everyone else, use `git fetch` to bring down new changes.
12. Check the status. See that origin has some news for us. At this
stage, nothing has changed locally, except that git knows the latest
news from origin.
13. Type `git merge` to bring the changes into the local branch.
14. See the new file.

## Simultaneous work

What if both people make changes at the same time?

1. Do this. Everybody (create if necessary and) edit a file named after
them.
2. Everyone `git push`. The first to push will have no problems.
3. When `git push` complains about being unable to fast-forward, it's
time to:
4. `git fetch`
5. Check the status. See that we have a commit, and origin has a commit
for us.
6. `git merge` to bring all the changes together.
7. `git push` to share the result.
8. Everyone else, `git fetch` and `git merge` to update to the latest.
Note that when you're quite sure you want everything from
origin into your local branch, then `git pull` is a shortcut for `git
fetch; git merge`. I don't recommend it, because of conflicts.


# References
 [Good practice for commit
messages](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
