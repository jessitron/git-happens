---
layout: illuminated
---

## Play with Configuration

## print it out

   git config -l

## create your own parameter
Create your own parameter. Set it to something different at the system,
global, and local levels. See which one wins.
For instance,

    git config --system favorite.color blue

Check it at the different levels too:

    git config --global --get favorite.color

Remove the setting from some places:

    git config --global --unset favorite.color

## make an alias
set up a shortcut in the alias section. For instance:

    git config --global alias.ll 'log --oneline --graph --decorate'
    git ll


