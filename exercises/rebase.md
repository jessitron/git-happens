-----
layout: illuminated
-----

## Exercise: Interactive Rebase

clone this git repository: https://github.com/jessitron/scalacheck.git
Checkout rebase/a

## Objective
Perform an interactive rebase from the tip of master.
- squash the two renaming commits together
- alter the commit message of bodilheimer (should be boodleheimer)
- edit the commit that has two changes, and break it up into two
  commits.
    - edit; then, when it stops
    - reset HEAD^
    - add -p to stage some of the changes.
        - s to split into more pieces
        - y to add the capitalization
        - n to not stage the last line
    - commit that
    - add the file to stage the last change
    - commit that
    - continue rebase.
