---
layout: post
title: UX on websites
---

Rant time!

So, today I wanted to use [IssueHunt](https://issuehunt.io). The website
allows developers to post tasks and everyone can back the task up with money.
So that whoever solves the tasks, gets paid by the backers. If you are someone
who wants to solve one of those tasks, you have to search for one that suites
you. The site allows searching through the tasks with a paginated list and a
component on the left side of the website where you can select your target
languages.

![Screenshot of the website](https://raw.githubusercontent.com/bios-marcel/Bios-Marcel.github.io/master/images/uxonwebsites/thepage.png)

This is what the site looks like. The width of my browser window is *960px*
and is used as follows:
* *128px* (13,3%) - Whitespace on the left
* *160px* (16,6%) - the filter component
* *30px* (3,1%) - whitespace
* *510px* (53,1%) - the actual content
* *128px* (13,3%) - Whitespace on the right

__Not all numbers might add up to the full 100%, but you get the point.__

So about half of the website is content, the rest is mostly whitespace and
the filter component. The filter component doesn't even use the height of the
site well. It would've been much better at the top, so the full width could be
used for the content. This is fine for a fullscreen window, but not for small
windows. Oh by the way, responsive design doesn't mean "scales down", it means
to accordingly adapt the application depending on your current display size
and device.

If you wonder why I'd use such a small browser window, that's becuase I was
watching some stuff on YouTube while browsing IssueHunt. And no, I don't
want to only do one thing at the same time.

Okay, next is he filtering component. It lists languages that you can
click to select them. It is basically like a list of checkboxes ... unless you
click the first item called `All languages`, because that will deselect all the
items below. Since there are many many technologies, not all of the available
items are in that list. There is a secondary mcomponent, that shows the rest of
the languages and allows you to search through them. Just like the list above
, you can select multiple items. Every time you select an item, the whole site
will refresh. Since there is no button to apply the new filter options, this
makes sense. However ... an apply button would have made more sense.

Oh and the filtering would display any task that fits one of your selected
items, which wasn't obvious, since the UI indicated that in no way.

There are other ways to get the same functionallity, but less horrible. Look
at stack overflow for example. If you want to chose your tags, you get a
textfield where you can enter a word and it will show you all available options
that contain the word you have entered and it will even display a little piece
of explanation. If you want to delete one of the tags, you just hit the `X`
on one of the tags. The component barely takes any space and does exactly what
it should do.

So far so bad. Now I wanted to look at the actual content, first I looked at
the available issues for JavaScript, just to see how many there are. Right
below the list is a pagination component:

![pagination component](https://raw.githubusercontent.com/bios-marcel/Bios-Marcel.github.io/master/images/uxonwebsites/pagination_currently.png)

It uses *180px* of the screens width, no matter what the width of your window
is. You got two buttons, one for left and one for right. At first I thought,
that those mean backwards and forward. However, they didn't. You could've just
wrote `first` and `last` on them ...

Okay, since the component only displays 3 items, you have no clue how many
pages there are, even though there was enough space to display more or even
display the first page, the last page and the current range where you are.

After chosing another language than JavaScript, it displayed the same things
again, a `1`, a `2` and `...`. However, after chosing the second page, the
three dots became a `3`. Very confusing as well. You could have just shown me
three items for three pages.

Now this is what the component should've looked like if there were more items,
than the page could actually fit:

![The dream I have](https://raw.githubusercontent.com/bios-marcel/Bios-Marcel.github.io/master/images/uxonwebsites/pagination_dream.png)

With this you'd be able to:

* See on what page you are right now
* See and visit the first page
* See and visit the last page
* visit the previous and next page
* See what page you are currently on

Obviously it should always use as much space as possible, in order to show as
much content as possible. You could theoretically even allow to jump to a
specific page directly, but that's probably useless, since the pages just
contain random items and there shouldn't be a reason to go to a specific page.

And if we have enough items to fit them onto the page, just display all items
without unneccesarily complicating the component.

So what did we learn? Just because something looks good, that doesn't make it
useful. Next time think about your UX before implementing the UI. And yes, I do
in fact think, that the site looks visually pleasing.

