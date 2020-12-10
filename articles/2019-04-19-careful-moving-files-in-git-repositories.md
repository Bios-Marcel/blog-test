---
layout: post
title: Be careful when moving files within a git repository
---

So, today I learned something interesting about git that I have been doing
wrong way too often without even noticing it.

Imagine the following scenario:

You have a file called `hello.go`, it greets the user with the very simple and
static sentence `Hello user.`. At this point and time the commit history for
the file looks like this:

```
~/code/hello (master)$ git log --follow hello.go
commit 03c325f415ca2418fa9bf9f759ca1fc16f50c8e6 (HEAD -> master)
Author: Marcel Schramm <marceloschr@googlemail.com>
Date:   Fri Apr 19 19:11:06 2019 +0200

    Add initial implementation that simply greets the user with a static sentence.
```

Next you decide that a static greeting is quite boring and unpersonal. So you
now have new requirements. The application should greet the user differently
depending on the current daytime. The greeting it uses between 6am and 11am
should be `Good morning user.`. Starting at 12am til 5pm it should use
`Hello user.` and starting 6pm it should use `Good evening user.`. On top of
that it should be able to take the users name via a parameter that can be
passed on startup. So you rewrite your code accordingly.

Now you decide that a more fitting name for this file would be `greeter.go`,
since it doesn't simply say `Hello user.` anymore, so you rename it:

```
~/code/hello (master)$ git mv hello.go greeter.go
```

Your changes were made and your file has been renamed. Now you wanna commit
this, so you add your new file to the staging area:

```
~/code/hello (master *+)$ git add greeter.go
```

Finally you commit:

```
~/code/hello (master +)$ git commit -m "Rename hello.go to greeter.go, since it is more fitting. Change output depending on the daytime and optionally accept a username."
[master d003cc6] Rename hello.go to greeter.go, since it is more fitting. Change output depending on the daytime and optionally accept a username.
 2 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 greeter.go
 delete mode 100644 hello.go
```

Fine, you are good to move on! Next day you wanna see the history, so you call
git log on your `greeter.go` file:

```
~/code/hello (master)$ git log --follow greeter.go
 commit 33a3c028ef060c600164f0f7c7757012426f319c (HEAD -> master)
 Author: Marcel Schramm <marceloschr@googlemail.com>
 Date:   Fri Apr 19 19:29:26 2019 +0200
 
     Rename hello.go to greeter.go, since it is more fitting. Change output depending on the daytime and optionally accept a username.
```

Since, there wasn't enough similarity between the old file and the new file,
git didn't really notice that this is still the same file, but with different
contents. Since `git mv` is basically just an alias for `git rm` and `git add`.
So if you only were to do small changes, this might work fine. Anyway, you will
still have all changes in your full repository history.

In order to prevent this loss of file history you simply have to first commit
the rename of the file and then do your changes. Never do renaming and changing
of the content in one commit.
