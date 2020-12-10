---
layout: post
title: git reset --hard isn't that hard
---

Like the experienced git user that I am, I accidentally deleted some of my
code. I did this by running `git reset --hard HEAD^^`. I meant to only insert
one circumflex, but that key acts differently on windows than it does on linux.
Sadly I am already way too used to the linux behaviour, which only inserts one
circumflex after hitting the key twice.

After a short search on StackOverflow, I found out, that reset doesn't
actually drop a commit. Instead the branch will just stop tracking that
commit. Meaning that you can still access the commit, as long as you still
have the commit-hash or you can try finding it with `git reflog`.

After reading the man-page for `git reset` this also makes sense, since all
that `git reset` is doing, is to modify the index and optionally your working
tree.

However, this is even more interesting, when you are deleting a branch. A
branch is really nothing more than a chain of tracked commits. So even after
deleting a branch, you can still find the commits in the reflog. And simply
`git cherry-pick` whatever you need.
