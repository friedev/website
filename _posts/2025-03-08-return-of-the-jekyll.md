---
title: "SSG Wars: Return of the Jekyll"
date: 2025-03-08
tags: ssg website
toc: true
---

Four and a half years ago, I [switched away from Jekyll]({% post_url 2020-09-22-goodbye-jekyll %}) to [create my own static site generator]({% post_url 2020-10-03-custom-ssg %}) out of shell scripts and duct tape.
Now, the epic saga has come full circle, and I am once again using Jekyll to generate my website!

Here's everything that's happened in the meantime.

## The Story So Far

(If you don't care about the lore, you can [skip](#a-new-website-design) the prequels.)

### The Maugriftium Menace

After making the first version of my SSG script in October 2020, I continued augmenting my website with various categories pages, including music and videos.
Predictably, this caused my my original shell script SSG to balloon into a monster haunted by [HTML-parsing regex](https://stackoverflow.com/a/1732454) and [plagued by backslashes](https://docs.python.org/3/howto/regex.html#the-backslash-plague).
So much for "elegance" and "minimalism", huh?
By abandoning Dr. Jekyll, I had become Dr. Frankenstein.

In general, the larger a shell script gets, the more the flaws of the shell as a programming language begin to rear their heads, and in this regard, my script was well on its way to attaining hydra status.

#### The Purge
I had stopped using version control for my website at this point (*the horror!*), so I don't have exact dates here, but sometime after April 2021, I decided to simplify my website, removing the blog, videos, Stagit index, and all other non-project pages.

There were a variety of reasons for this culling.
For one, I had realized that I was the antithesis of a consistent blogger, and I decided I'd rather have an "evergreen" website than one that looks neglected and malnourished.
For another, I was gradually wanting to appear more professional online, and the goofy tone I was using on various pages was unbefitting of a proper corporate tech bro.

In any case, trimming all this juicy fat from my site allowed me to lop a few heads off the hydra that was my SSG.
Nonetheless, I still needed it for adding a header and footer to each page, and for generating my project index.

I also took down some of the [servers I was running]({% post_url 2021-02-14-site-updates %}#servers) --- IRC and Mumble, but not email.
It was a good learning experience to set them up, but they were predictably barren, given the nonexistent nature of my "fanbase", and they were creating a potential security vulnerability just by sitting there unmaintained.
There was a time where I was regularly chatting with one friend on my IRC instance, but we eventually went back to the increasingly commercialized but vastly more convenient option of Discord.

### Attack of the Alpines

#### frie.dev
In the late spring/early summer of 2022, I transitioned away from my "Maugrift" identity to my current "friedev" identity, and with that came a new domain for this website.
A new domain needs new branding, so I made some updates to the layout, CSS, and avatar/favicon.

The rebrand to "friedev" was driven by that same desire to look more professional, and it ticked most of the boxes for a decent alias.
I'm a sucker for double entendres, and "frie", in case it's not obvious, is 1) the first 4 letters of my last, and 2) pronounced "free", creating the phrase "free dev", which is pretty apt considering I'm a big fan of free software.
Also, I only later learned that "frie" in Danish does, in fact, translate to "free".
Convenient!

As for setting up redirects, I, uh, didn't.
I just let the domain expire to save an entire $10 a year (oh yeah, epic win for frugality).
I wasn't particularly worried about people not being able to find my new domain, since I was (and still am) basically a nobody on the internet.
I figured people who actually knew me would be able to find me through my other profiles that linked to the new site (or because I would've already excitedly told them "I have a new website btw").

One consequence of relinquishing maugrift.com is that apparently there are trolls out there who look for sites that people used to own and buy them up.
Who would've guessed, right?
It's not like it's the internet or something.
At one point, it was serving some Chinese web games, and now some Chinese sports... game... thing...?
I don't know.
You probably shouldn't go there.

#### Alpine Linux VPS
I took the opportunity to spin up a new, cheaper VPS, still using [Vultr](https://www.vultr.com/).
This time, I installed [Alpine Linux](https://www.alpinelinux.org/) instead of Debian.
It's very light, and while I hadn't had a great experience using it as a desktop distro, it fit the server use case pretty well.

On Alpine, I faced my greatest challenge yet: setting up an email server.
On Debian, I had been able to run the convenient [emailwiz](https://github.com/LukeSmithxyz/emailwiz) script, but it wouldn't work out of the box on Alpine.
Instead, I spent an evening or two running the script one relevant line at a time, interspersed with frequent checks of Alpine Linux's somewhat sparse documentation on the subject of email servers.
OpenDKIM was my true nemesis, but I eventually got it working, and I was *pretty* sure the configuration was good enough.

#### When the world needed him most, he vanished...
Around this time, I had entered my recluse arc, in which I minimized my online presence by deleting as many accounts and public profiles as I could justify to myself.
I may dig into my motivations for all this in another post, but in short, it boiled down to fear and antiestablishmentarianism (not to be confused with its more notorious cousin).

This website was one of few exceptions to my vendetta, since it was something I had nearly full control over, and without any other profiles, I'd have nowhere else to share my ostensibly cool stuff.
My itch.io pages and GitHub repositories were not so lucky, and joined the casualties of this purge.
Surely, I figured, any sufficiently cool contributor would know how to use the obscure [git send-email](https://git-send-email.io/) command, right?

#### Server-side includes
In the months prior to the transition, I had discovered [server-side includes](https://en.wikipedia.org/wiki/Server_Side_Includes), or SSI, allowing me to replicate one of the most useful features of Jekyll.
Now, my SSG script didn't need to be the thing that added headers and footers to pages; the pages themselves could tell nginx to do it with directives like `<!--#include virtual="content.html" -->`.
Although the versatility of this feature was limited, it still radically improved my site organization.

#### README generation
Without GitHub repos, there was now no easy way to read the READMEs for my projects without cloning them.
And so it was here that I implemented the most useful feature of my SSG: generating project pages from their READMEs.

My previous approach to writing the content for my project webpages, as far as I can recall, was to manually adapt the content of each markdown README into an HTML webpage, potentially adding or removing various tidbits in the process.
But of course, copy and paste is evil!
Under this system, my project webpages could fall out of sync with their respective READMEs, requiring me to update both places independently.

Thus, using the [revolutionary new technology](https://kristaps.bsd.lv/lowdown/) of converting Markdown to HTML (the same approach I had once [criticized]({% post_url 2020-09-22-goodbye-jekyll %}#the-choice-of-html)), I could easily keep my webpages in sync with their READMEs.
Crucially, this also made it less annoying to add new projects to my website, making me more likely to actually release things.

#### pup
Up to this point, regex was still a necessary evil to allow my SSG to generate the index of projects on my homepage.
The script would search through each project page and clumsily extract various bits of information, like the title, release date, and excerpt, and then trim them up and package them into a neat little capsule on the front page.

Fortunately, I found (and actually got around to implementing) a better way to do this step that didn't involve nearly as much `grep`'ing and `sed`'ing: [pup](https://github.com/ericchiang/pup)!
pup allows you to extract information from HTML using CSS selectors, which just makes way more sense.
This change made the whole script a fair bit nicer, though some might call it lipstick on a pig (or a dog, in this case?).

### Revenge of the VPS

Since the 2022 changes, I think things remained mostly the same through 2023, with only the occasional project update.

#### Migadu
In May 2024, I started using [Migadu](https://migadu.com/) to run my mail server.
(So much for that grueling Alpine Linux email installation, I guess...)

The desire to transition away from self-hosting my email server stemmed from laziness and risk-aversion (i.e. fear, again).
Basically, I had decided that email was too important to leave in my own hands as a less-than-competent Postfix administrator.
Migadu provided an enticing alternative without the arbitrary restrictions and pricing schemes of most other email providers.
So far, I've had a good experience with Migadu, but that's a subject for another blog post.

#### GitHub
This left me with the realization that all I was using my VPS for was to host my website and Git repos.
I had already been considering putting my repos back on GitHub, having begrudgingly acknowledged its ubiquity and the power of its network effect.
If I wanted anyone to actually be able to find my repos and get any use out of them, let alone contribute, I would need to return to the dark side.

Fortunately, however, [Git itself is fundamentally decentralized](https://drewdevault.com/2018/07/23/Git-is-already-distributed.html) and repos are pretty portable, so it's not like creating a GitHub remote for my repos meant forever surrendering them to Microsoft.
I could easily create other remotes on other forges, and mirroring my repos across them probably wouldn't be too painful.
And so, in November 2024, it was done: I was back on GitHub.

This left my VPS with very little to do --- just hosting my website.
And thus I decided to put it out of its boring existence and save a whole $5 per month (another common frugality W).

#### GitHub Pages
Since I was using GitHub again, it seemed only fitting to host my website on GitHub Pages.
(I did consider some alternatives, and I'll probably talk about them in another separate post, but GitHub Pages was just the easy and obvious choice here.)
And thus the cycle was almost closed, leaving only...

One problem: GitHub Pages didn't support SSI.
*Well,* I thought, *if I'm back on GitHub Pages, maybe I can use its CI/CD to run a basic SSG that just handles includes?*
Of all the SSGs I bothered to look at, Jekyll seemed like the easiest one to use to implement the basic include functionality without having to overhaul the rest of my website, and so I added it.

And that's how things have been for the last few months.
Until now!

## A New Website Design

Behold: yet another website design!

This time around, I have embraced the power of Jekyll to generate a fully-featured site in a relatively elegant way.
As is required by GitHub Pages (on the free tier at least), [the repo](https://github.com/friedev/website/) is public, so you can see exactly how I put it all together.

### The Strange Case of Dr. Jekyll

I chose to fully commit to using an off-the-shelf SSG because I realized I would never be able to compete with their enviable feature sets in a maintainable way, especially not with a shell script.
Besides, I'm not really interested in coding an SSG myself; after all, why reinvent the square wheel when there are lots of round wheels available for free?

This has meant recognizing and abandoning my tendencies toward extreme minimalism and independence.
I had gotten to the point of embracing these things for their own sake, all while practicality had taken a back seat.
This shift in mindset has been brewing over the last year or more, and has culminated in various changes to my workflow, all of which I've been very happy with.
I think yet another article is in order to talk about them all.

After deciding that I was going to use an SSG, I was inclined to try Hugo for various superficial reasons.
It has more stars on GitHub than Jekyll, it's written in Go instead of Ruby, and it has a proper package in the `extra` repository on Arch Linux.
Despite these nice things, I found myself a bit intimidated by the sprawling organization of the documentation as I started reading it, and slightly put off by the apparent requirement of using a theme.
It seemed like it might've been more difficult to port my existing site to Hugo than to gradually transition to using more of Jekyll's functionality.

Now, I probably should've put more effort into prototyping a Hugo site locally and seeing how easy it would be to port my existing site to Hugo... but I didn't feel like it.
Jekyll's docs were more friendly, and since I was already using it for includes, it was easy to slowly start trying out more of its features.

### No themes?

I did strongly consider using a third-party theme for Jekyll, specifically the [Chirpy](https://chirpy.cotes.page/) theme.
I think it looks fairly attractive and has a lot of extra little add-ons to Jekyll that would be nice.

Unlike Hugo, I did put some effort into mocking up a site with Chirpy, but I eventually decided against it.
Mainly, it just had too much going on under the hood for me to wrap my head around, which I knew would get in the way of me customizing things how I might like to.
Furthermore, I knew I would feel kind of dirty having a site with so much frontend code --- over 250 kB of JavaScript and CSS (after minification!).

Maybe that's just my old minimalist ways dying hard, but I feel much better knowing that I've made everything on my site, and I know how it all works.
And fortunately, Jekyll has turned out to be powerful enough to do everything I needed.

### Screw it, I'll make my own theme

Despite decrying JavaScript and CSS bloat just now, I did decide to add icons to my site from [Font Awesome](https://fontawesome.com/).
That adds about 380 kB of web fonts and CSS that have to be downloaded on first page load (which, in fairness, Chirpy would have also loaded, in addition to its custom JavaScript and CSS).
I stand by this decision though; they just look nicer, and, more importantly, I can fit more icons into the same space compared to textual links.
For most people, they're just as readable as text, if not more (one could even say they're... iconic?), though I do apologize if it interferes with screen readers and the like.

In any case, there's also plenty of new CSS styling going on here, all lovingly hand-crafted on top of my previous stylesheet.
I kinda liked the blocky theme I had going on, but I also dig the slightly rounded aesthetic I've come up with.
(If Microsoft can get away with changing `border-radius` and passing it off as a whole new UI, then why shouldn't I?)
Same with adding borders to stuff; I just tried it on a whim and I think it looks kinda nice.
I'll probably switch to Sass sometime Soon™, but I'm keen to get this redesign out the door first, since switching to Sass would just be an internal refactor.

Long-time knowers of my existence may have noticed that I've brought back the old Maugrift avatar!
For a while during the initial friedev era, I had switched to a simple white-on-black @ sign as my avatar, in reference to 1) the first letter of my name, and 2) the classic roguelike player symbol.
However, I eventually decided it was too generic, and so I've switched back to the space knight logo I made for my Maugrift persona, which is unique to me and still looks cool (well, at least *I* think it does, and I have impeccable taste, not to mention a great sense of humility).

### Gone but not forg--- wait, it's not gone?

Funnily enough, I'm still using the last remnants of my SSG script!
At this point though, it's only to keep the READMEs up to date --- no more HTML parsing (phew).

One slightly ugly, but useful, feature is looking for links in each README that point to other files in the repo (e.g. `LICENSE.txt`), and redirecting them to the corresponding file on GitHub's web view.

Thanks to the power of Jekyll layouts and front matter, I'm able to generate each project page without any writing any content manually.
All I have to do is specify the metadata and the layout does the rest!

## The Blogger Strikes Back

If you're reading this, you just *might* have noticed that the blog is back!
I've had various things I've felt like writing about for a while now, and this seems like a nice place to do it.

Don't expect any kind of consistency, at least not yet.
As I've discovered, I'm not exactly the most consistent blogger, nor the most consistent person in general when it comes to working on side projects.

That being said, I *have* been working on some games in my spare time, which I may start writing about on this blog when I feel like procrastinating on the games themselves.
And, although the blog has been gone for a while now, that hasn't stopped the site from fulfilling it's main purpose as a project portfolio.
Over the last few years, I've published a decent number of projects, which you can check out on the [Projects](/projects) page if you haven't already.

If you want to get notified about future blog posts, you can subscribe to the [RSS feed](/feed.xml), generated with the help of the [jekyll-feed](https://github.com/jekyll/jekyll-feed) plugin.
(And if you don't use RSS, you really should try it!)

If you made it this far, thanks for reading this unexpectedly long article.
Until next time!
