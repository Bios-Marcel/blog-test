---
layout: post
title: Don't refork a GitHub repository every time you want to contribute
---

Sometimes people contribute to one of my projects, and every time that they
want to contribute, they delete their fork and fork the project again.

They usually do this because they don't know how to easily get an up-to-date
master branch again. Since it's much easier to just hit "delete" and "fork"
again, that's what they do instead.

However, this problem usually occurs when people start working on the `master`
branch instead of a branch specifically made for their PR.

So the next time you want to work on a fork of some project with the intent to
contribute your changes via a PR, do the following instead:

```shell
# Clone your fork
git clone git@github.com:/you/project
# Add the original repository as a new remote
git remote add original https://github.com/someone/project
# Now you'll have the remotes "origin" (fork) and "original" (original)
# We assume that your current master branch has no exclusive changes
# Now update your master using the originals masters state
git pull original master
# Now that you have an up-to-date master, create a new branch of that
git checkout -b your_new_feature
# This creates a new branch called `your_new_feature` and checks it out
# Now start implementing your feature and commit the changes.
# When you are done, push your changes to the fork
git push --all origin
# --all will push all branches to the remote
# Now create your PR via GitHub. As soon as it gets accepted into
# master, you can repeat the same procedure starting at
# `git pull original master`
```

This way you won't have to worry about both remotes having different
commits, merge commits or whatever, since all your changes happen on a
throwaway branch anyway.

In case you already have a poluted `master` branch, you can do the following:

```shell
# Check the originals master out
git checkout original/master
# This will bring you into a "Detached HEAD" state, meaning you aren't on a
# branch, but on a specific commit you could say.
# Now delete master locally
git branch -D master
# After deleting master, we use our current state to recreate it
git checkout -b master
# Now we'll locally have an up-to-date master
# Now we push, but we need to apply `--force`, since our commit will delete commits that already exist upstream.
git push --force
```

I hope this helps ;)

If you have an easier way of doing those things, leave a comment!
