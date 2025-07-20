---
title: Terminated 2.0.0 released
date: 2025-07-20
tags: games projects terminated
toc: true
---

`ERROR: FAILED TO TERMINATE ROGUE AI. INITIATING WEAPONIZED SHUTDOWN PROTOCOL.`

[Terminated](/terminated) is a top-down arena shooter in which you play a sentient robot cast into a scrapyard.
How long can you survive against the endless onslaught of mindless drones sent to terminate you?

For the few who remember 1.0.0, you'll find that 2.0.0 delivers a familiar robot-slaying experience, freshly tuned up and given a new coat of paint!

[Play now on itch.io!](https://friedev.itch.io/terminated)

In this post, I'll talk probably too much about the history of Terminated, the new features in 2.0.0, and why this release is happening now of all times.
Sound good?
Alright, let's go!

## Terminated 1.0.0

For those unfamiliar, Terminated was my first ever solo Godot project!
I started working on Terminated in 2021, around the same time I was developing [Minieval](/minieval) with my team from the [UNL Game Dev Club](https://unl-game-dev-club.github.io).
It served as a useful little side project for me to learn about many features of Godot that we weren't otherwise using in Minieval, which --- considering Minieval was a turn-based, tile-based game --- was a lot!

### Inspirations
I was initially inspired to make an arena shooter by [Devil Daggers](https://devildaggers.com/), created by [Sorath](https://sorath.com/), which I was hooked on at the time.
(I still think it's a near-perfectly designed game, although I bounced off the arguably perfect-er sequel [HYPER DEMON](https://hyprd.mn/).)

I directly ripped off some basic mechanics, like holding left click to shoot a machine gun vs. tapping it for a shotgun blast, and having an arena made of square tiles with an edge that you can fall off.
My goal wasn't to create a perfect 2D clone of it though --- after all, noted Devil Daggers player [Bintr](https://www.youtube.com/@BintrMagMorganorts) had already made a pretty faithful adaptation called [2DDD](https://www.youtube.com/watch?v=AdUhOtKY0ko).

Nonetheless, I find it interesting to see what foundational design decisions this inspiration led me to.
In the contemporary, post-[Vampire Survivors](https://store.steampowered.com/app/1794680/Vampire_Survivors/) era, certain aspects of the top-down shooter genre are becoming almost ubiquitous, it seems.
As one of the (few?) people who wasn't a huge fan of Vampire Survivors, I think it's crazy how many contemporary top-down shooters don't even have aiming or meaningfully different enemy types.
On the other hand, Devil Daggers only has one upgrade "path", and Terminated doesn't have any (yet).

There's also the feel of the experience.
For instance, Devil Daggers and Terminated don't allow you to pause mid-game, because that would interrupt the flow and give you reprieve from the games' essential tension, and they can get away with it because the runs are ([relatively](https://www.youtube.com/watch?v=eHgjezimY58)) short.
In comparison, Vampire Survivors (and presumably its descendants) has a mandatory pause every time you unlock an upgrade, and a successful run generally lasts 30 minutes.

All that's to say, despite Vampire Survivors-likes being a popular project for first-time game devs, Terminated was not such a project.

I'd be remiss if I didn't mention another more obscure game that became a bit of an inspiration as Terminated took shape --- [BSD robots](https://en.wikipedia.org/wiki/Chase_%28video_game%29).
This was a simple turn-based terminal game where robots would move straight toward you from all sides.
If two robots ran into each other, they'd collide and create a scrap heap that other robots could collide with.
Your main tool was a teleporter that would put you at a random spot anywhere in the level --- including potentially right next to a robot, immediately ending your run.
Therefore, you had to use it sparingly.

This idea of bumbling robots crashing into one another while you simply avoid them came to shape the design of certain enemies in Terminated.
Aside from the basic enemy, every other robot has the potential to destroy others.
There's a crusher than can simply drive through hordes of tiny robots, a bomb that destroys all enemies in its radius, and a laser that destroys all robots in a line.
These enemies all target the player, but the collateral carnage of the other robots is fun to behold.

### Initial Release
Being an action-packed, real-time game, Terminated had a pretty good "fun factor" right out of the gate.
Anyone could dive right in and play without reading any walls of text.
Despite this being a pretty low bar, Terminated was the first game I'd made that well and truly cleared it (the competition being Minieval, [Minius Maximus](/minius-maximus), [GeneriCrawl](/genericrawl), and [EverSector](/eversector)).
Because of this, Terminated was my go-to game to show off at club events for a while.

I eventually released Terminated 1.0.0 on itch on October 4, 2021, and I also put the source code up on GitHub.
As expected, there wasn't really any reception to speak of, especially considering I wasn't putting any effort into promotion (which I'm still not).
It was just nice to put something out into the world and have it available for people to play.

After the release, I left Terminated as it was for a while, spending my free time on various non-game projects instead, including [Arghonaut](/arghonaut) and [Boost](/boost), as well as doing some more unrelated tinkering in Godot.

However, as is always the case with game devs and side projects, I still had ideas for more things I wanted to add.
And so, starting in March 2022, I got to work on Terminated 2.0.0!

## What's New in 2.0.0?

### Art
The first thing I changed for Terminated 2.0.0 is also the most noticeable: the art!
I replaced all the dark gray on dark gray with... dark gray on light gray.
It may not sound terribly exciting, but I do quite prefer the contrast.

### Flocking
The basic enemies (little spider-bot things in 2.0.0) now move in a [flock](https://en.wikipedia.org/wiki/Boids), much like the skulls in Devil Daggers.
This looks cooler and also makes their movement more predictable to the player, allowing you to survive more easily while still having the fun experience of facing down a huge swarm of robots.

### Flight
Sometimes, just tweaking numbers can have a big effect on game feel.
In this case, I mainly just sped up the movement of the player and the enemies.
But also, I added a "flight" mechanic.
Now, when you move without shooting, you get a significant speed boost to help you avoid enemies and discourage you from just holding down the shoot button, as you could in 1.0.0.

### Soundscape
The original sounds for Terminated came from [jfxr](https://jfxr.frozenfractal.com), which gave it a retro, chiptuney sound.
I wasn't satisfied with it though.
I knew I could never recreate the immersive soundscape of Devil Daggers, but I wanted to create something meatier and more grounded.
So, I redid the sounds for just about everything in the game!

### Walls
Unlike Devil Daggers, the arena in Terminated has walls now.
No longer can you anticlimactically fall off the edge of the world while enemies fly freely over the abyss.
Instead, the opposite is true!
Small enemies will break if they collide with the walls, but you can bump into them no problem.
Though you may still want to avoid the perimeter, because that's where all the enemies spawn.

> **Historical note:**
> All the above changes were made back in March 2022, but from here on down, everything was done *yesterday*!
> More on that later...

### Random Waves
The enemy waves in Terminated 1.0.0 were entirely hard-coded; the enemies that spawned at any given time were always the same, even though they would be different positions.
This was a holdover from Devil Daggers, which probably had just a *bit* more thought put into the pacing and balance of its waves.
In my case, I'm less interested in making a perfectly fair spawning system for players to compete on a global leaderboard, and more interested in something fun and varied to play for myself.

Therefore, I made it so each wave spawns up to a certain number of "difficulty" points worth of enemies, increasing with each wave.
This way, the challenge increases steadily and the waves vary more each run.

I had the idea to implement this system after seeing the same thing done in a game made by some UNL Game Dev Club friends: [cyber_serpent](https://store.steampowered.com/app/2667680/cyber_serpent/).
I'm sure it wasn't the first to do random waves this way, but it was the first game where I identified the system and saw it put to good use.
(Go check out cyber_serpent by the way; it's free and even more fun than Terminated!)

### New Main Menu
While I have a certain fondness for the utilitarian, non-modal main menu of Terminated 1.0.0, I felt the need to make a proper menu for 2.0.0.
I'm not exactly known for stylish menus, but I think this one turned out nicely.

### Bigger Level
This is another simple number tweak, but increasing the map size by 50% allows more room for chaos to build up while giving you some extra space to survive and experience it.

### High Score Tracking
This is a pretty small thing, but important for a game like this!
Now you can try to improve your PB without having to write in down outside of the game like a Neanderthal.

### Controller Support
I suppose they don't call 'em "twin-stick shooters" for nothing!
I don't play with controller, so this was a bit of an afterthought, and I don't know exactly how it's *supposed* to feel, but I think I got it working pretty well.
If you're a true twin-stick player, let me know what you think.

## Why 2.0.0 Now?

As I mentioned above, most of the work for 2.0.0 was done in two chunks: one in March 2022, and one literally yesterday.
Considering the apparent 3 year hiatus, you may be wondering why I didn't release 2.0.0 sooner.
In fact, asking myself that very question is partially why it came out today!

### Intermittent Development
In the time since 2022, I worked on Terminated *very* intermittently, occasionally taking a few hours here and there to refactor or bugfix my noob-level Godot code.
Remember, this was my first solo Godot project, and I'm still using the same codebase as when I started!
Whether or not that was a wise use of time, compared to starting again in a new repo, is another matter... but by now I've shaped it into something that's fairly nice to work with, so it's a moot point.

Overall, this practice of gradually tweaking and refactoring old projects is pretty typical for me.
Along with creating entirely new projects, I tend to find it less intimidating than making big additions to big projects.
Of course, you need to make big additions to be able to build the most impressive creations in the long run, hence it's a bit of a problem.
I doubt this is just a "me" thing; it's probably some combination of software architecture hurdles and executive dysfunction.

So when I sat down yesterday, looked at my (long) list of Godot projects, and chose Terminated to open on a whim, I certainly was not planning to have a whole 2.0.0 release ready by the end of the day.
I was just hoping to fix a few game-breaking regressions I knew about and get it to a functional enough state to share with people again.
But after fixing said bugs and making various improvements as I saw fit, I began to realize that the game was actually in a pretty solid state!
Solid enough, perhaps, to release...?

### Grand Plans
Part of why Terminated has been in development limbo over the last few years is because I have some really cool ideas that I think would give it a unique gameplay loop and an identity beyond just a typical top-down shooter.
I don't think I'm ready to talk about this new design just yet, and I'm probably making it sound cooler than it is, but it does make me a little excited.

The prospect of implementing it, however, despite being entirely doable given my skills and experience, is exactly the kind of intimidating thing that can put me off of working on the game as a whole for indefinite time spans.
After all, wouldn't it be better to release all this cool new stuff in one go?
And maybe take it seriously and do a commercial release or something?
As you can probably guess, those kinds of thoughts aren't really helpful in actually getting me to sit down and work on things.

Putting those ideas aside and lowering the bar for 2.0.0 allowed me to realize that there wasn't actually that much more work that needed to be done to get the game to a release-able point.

Long story short: I've realized I shouldn't let my aspirations for what Terminated could eventually be stop me from sharing what it is now.
And that's why I decided to just go ahead and make a release out of it!

Alright, that's enough introspection for what should probably be a quick post about a video game update.
Onward!

## What's Next?

> 3.0.0 when???

If you're hyped about those tantalizingly vague ideas I mentioned in the last section, don't get your hopes up too much.
Like I said, it'll take a good bit of work to add all that stuff, and it's not necessarily my top priority now that I've reached the milestone of having Terminated playable once again.
I've got a bunch of other side projects competing for my attention, and it's likely my next release will be something else entirely.
So keep an eye out for that, I guess.

See you then!
