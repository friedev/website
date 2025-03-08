---
title: Goodbye Jekyll, Hello HTML!
date: 2020-09-22
tags: website ssg
toc: true
---

Ahh, sweet minimalism!

It amuses me that the [first post]({% post_url 2020-05-10-hello-there %}) I wrote on this site is all about the infinite power of [Jekyll and GitHub pages](https://help.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll), and now here I am running a pure static HTML site off of a VPS.
Might as well take this chance to explain why!

## The Choice of HTML

I'll admit, I was slightly intimidated at first by the idea of writing a whole site in raw HTML.
Surely that's an archaic idea at this point in time, right?
Wrong!
Turns out it's super easy and actually way better.

For one, I have a lot more control over how I design the site and its content.
Before, I was at the mercy of Jekyll's markdown parser ([Kramdown](https://kramdown.gettalong.org/), I believe), which would compile things into whatever HTML it thought I wanted.
Most of the time, it guessed right, but sometimes I'd end up with situations like this...

I'd write the following markdown:

```md
- List item.
    - Sublist item.
```

Which Jekyll would convert into the following HTML:

```html
<ul>
    <li>
        <p>List item.</p>
        <ul>
            <li>Sublist item.</li>
        <ul>
    <li>
<ul>
```

In this case, I really just wanted a sublist:

```html
<ul>
    <li>
        List item.
        <ul>
            <li>Sublist item.</li>
        <ul>
    <li>
<ul>
```

(Note the extra `<p>` tag, which results in extra spacing, which looks weird in a longer list.)

Anyway, that's just one (probably overexplained) example of Jekyll being inconvenient.
And yes, I'm sure there's a way to make it work the way I intended, but I've just found it easier to make minor tweaks like this using HTML.
Probably because it's more explicit/verbose, and also far better documented.
(That's not to say Jekyll has bad documentation - far from it.
It's just that it's hard to compete with HTML due to the sheer number of people who use it and the number of other resources for it.)

Another complaint I have with Jekyll is that editing the CSS also seemed unnecessarily complicated.
With the [theme I chose](https://github.com/pages-themes/midnight/), I could add custom CSS pretty easily, but editing the existing CSS didn't even seem to be an option.
Even if I could have edited it, I wouldn't have known what elements and classes to reference.
And now, with very little effort, I've managed to create a website theme from scratch that I think looks basically just as good.

Lastly, HTML doesn't require any dependencies!
With Jekyll, I had to have a whole Ruby environment installed and run a program to generate the site.
Not only did that require more **b l o a t**, it also ended up being more work in the end, which kinda defeated the point of using a static site generator in the first place.

While writing static HTML requires a bit more typing (*gasp!*), it gives me way more control over the content I write.
Ultimately, it feels like SSGs don't really satisfy any sort of meaningful niche.
If you're really averse to working with "code," you're not going to want to use HTML *or* an SSG; you'd probably use some website builder software.
If you don't mind getting your hands ever so slightly dirty, why not go full HTML and skip the extra hassle of an SSG?
</rant>

## The Choice of a VPS

Similarly, the reason for choosing a VPS comes down to freedom (and some other stuff).

First of all, having a VPS is great in that it lets me do so much more STUFF besides just hosting a website.
Basically I'm paying for access to a (virtual) computer with a good internet connection, and thus I can do just about anything with it that I could do with a regular computer (and, in fact, more).

Second, it means I'm not bound to GitHub for hosting.
Instead of relying on them to have the options I might need, I can just change the server config directly.
I still have to rely on my VPS provider ([Vultr](https://www.vultr.com/)) to some extent, but nonetheless I get much more **p o w e r**.

*(I didn't choose Vultr for any good reason.
From my research, it seemed that the main VPS providers were DigitalOcean, Vultr, and Linode, but that they weren't much different.
While I can't speak to the quality of the other two, Vultr has worked perfectly fine for me.
I particularly like the hourly billing and the snapshot system.)*

Ideally, I would have my own physical server, but that's not really feasible for me at the moment.
One day...

## So Yeah

There's my completely unsolicited, slightly in-depth analysis of why I switched to HTML on a VPS.
As always, feel free to tell me why my opinion is wrong.
