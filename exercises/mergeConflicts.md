-----
layout: illuminated
-----

## Merge conflicts

    git clone https://github.com/jessitron/scalacheck.git
    git checkout conflicts/a

Use log to observe that there's a change and then a rename.
Also log conflicts/b to see the changes there.

    git merge conflicts/b

Now see the conflicts. Resolve them and finish the commit.
Notice that the file that was changed on one side and moved on the
other, it noticed.
