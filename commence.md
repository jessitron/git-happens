----
what does this do
----
# Let's git to work

Download and install git from [git-scm.org](http://git-scm.org/downloads)

## Global Configuration

> Git keeps global configuration in .gitconfig in your home directory. Don't edit this file directly. Instead use the configuration commands in git. Show and modify configuration with `git config.` The `--global` flag  

1. Everybody has to do these two things, or git will complain on every commit that it doesn't know who you are:

        git config --global user.name "John Doe"
        git config --global user.email johndoe@example.com

