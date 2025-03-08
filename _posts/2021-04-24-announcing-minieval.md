---
title: "Announcing Minieval: a tiny medieval city builder"
date: 2021-04-24
tags: games minieval projects
---

Minieval is a tiny medieval city builder, inspired by [Islanders](https://store.steampowered.com/app/1046030/ISLANDERS/).
You can play it online on [itch.io](https://maugrift.itch.io/minieval) (EDIT: currently unavailable) or check out the source code on [GitHub](https://github.com/friedev/minieval)!

In this post I'll be talking about the background of the game and the development process.
If you're interested in more details about the game itself, check out its [project page](/minieval) on my website.

Minieval has been developed over the course of the spring, starting around March 2 and releasing today, April 24.
Looking back on it, that's a lot less time than it felt like!
I developed the game along with a team from the [UNL Game Development Club](https://unl-game-dev-club.github.io) consisting of Kalen Wallin, Evan Mielak, Viet Ninh, Jackson Herman, and Ethan Fox.
I was the team lead and did most of the work on the game, but I want to thank all my team members for their help; without their contributions, the game wouldn't be as fully featured as it is now.

The original idea for the game came from [Islanders](https://store.steampowered.com/app/1046030/ISLANDERS), a minimalist 3D city builder.
It's a great little game and I'd recommend giving it a try if you haven't already.
The idea is to place buildings near other buildings that grant bonuses, while avoiding the interactions that result in penalties.
One Simple Trick™ I have to come up with game ideas is to take an existing game design and think of how it would work in another format or medium.
In this case, I thought, "what if Islanders was set on a 2D grid?"
It probably wouldn't be as visually appealing as its 3D counterpart, but it would surely be much easier for a team of amateur game developers to pull off.

Over time, the idea evolved a bit.
One of the first main differences that emerged was splitting up the game's resources into Currency and Victory Points (VP), rather than having a single resource that's used for constructing buildings and also used to determine your final score.
This split resulted in far more interesting strategic decisions; for instance, "Do I build this expensive building that gives me lots of VP, or do I continue to save up currency until I can afford a better one?"

Another major change of the format was the introduction of roads.
I imagine adding roads to a 3D game without some sort of grid or voxel system would be quite challenging, but in the 2D grid format, it wasn't as daunting a task.
In Minieval, you can create road networks that cause currency interactions to happen between all buildings placed next to any part of the road.
This means you can more easily scale up your city's income, but sometimes you want to avoid building on a road to avoid negative building interactions, and setting up the road network in the first place takes a lot of turns.

Minieval was created using [Godot Engine](https://godotengine.org), a powerful open source game engine.
As a fan of more programmatic approaches to game development, I was hesitant to choose Godot at first.
However, while developing Minieval, I've thoroughly enjoyed using it.
In my experience, it does a great job at simplifying several annoying parts of the development process, while still allowing you to control basically everything through code, which is a perfect balance in my opinion.
For an indie game dev team, I think it's a great option.

This game has been really fun to work on!
Surprisingly enough, I also think this might be the first game I've made that's fun to play in its own right, at least in my opinion.
Furthermore, this has been my first time using a proper graphical game engine ([Minius Maximus](/minius-maximus) doesn't really count since I pretty much just made the music).
Now that I'm more familiar with Godot, I'm looking forward to creating more games with it, so stay tuned!

There may be some small patches to Minieval over the course of the summer, but don't expect anything too major unless the game becomes super popular or something.
Like I said, this game has been a blast to work on, but I'm excited to work on some new ideas too!

Thanks for reading, and I hope you enjoy the game!
