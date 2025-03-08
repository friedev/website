---
title: The quest to write my own Static Site Generator
date: 2020-10-03
tags: ssg website
toc: true
---

Jekyll is overkill, but can I do better?

## Wait, What?

Despite bashing static site generators (SSGs) a bit in my [last post]({% post_url 2020-09-22-goodbye-jekyll %}), there are some useful aspects to them that I can't just ignore.
The biggest one for me has been copying all the boilerplate between HTML files (e.g.
the header).
Without an SSG, when I need to make a new page, I usually copy another HTML file and modify it.
As anyone who's done much programming before can tell you, this is a Bad Idea.
In particular, when I need to make a change to the header under this system, I have to go and *manually* change the header on *each* file.
This hasn't been a big deal since my site has been relatively small, but I could see the risk of technical debt steadily growing.

And thus, I set out on my quest to write a custom SSG!

As it turns out, it was actually quite easy to do.
Over the course of a day, I was able to whip up a shell script that would do everything I needed.

## How It Works

The core functionality of this script is copying every file named `content.html` on my website, adding a `header.html` and `footer.html`, and outputting the result to an `index.html` file in the same directory.
Thus, when I want to write a new page, I just need to write the main page content in a `content.html` file and then run `./ssg`.
Easy!

*(And yes, this means that you can go to the `content.html` file for any page on this and see the raw, unstyled page content.)*

One other convenient feature I decided to add is the ability to update the `<title>` tag with the name of the page.
Since I just use a `<h1>` tag for the title of most pages, I'm able to extract the page title from the `content.html` with a simple `grep` command.
Then, I run a corresponding `sed` command to substitute the name into the `<title>` tag.

## Why It's Great

1. First of all, this script acts as a perfect substitute for a full SSG, at least for my use case.
2. Second, it's short and easy to understand, so if I need to make any changes, it'll be easy to do so.
3. Finally, it's super minimal!
   I don't need to have any dependencies or fancy programming environments installed.
   Just a good old shell.

## "In Conclusion"

So yeah, making an SSG is easy and totally worth it!
If you don't feel like making your own, feel free to yoink mine.
It's not properly licensed or anything (yet), but I'm not gonna sue you for using my little convenience script.
As always, if you have questions, feel free to email me or whatever.
(I should probably make a comment form.
Hmm...)
