---
title: "Announcing MusiCLI: a MIDI sequencer for the terminal"
date: 2021-02-17
tags: musicli projects software
---

MusiCLI (pronounced "musically") is a simple, tracker-like, MIDI sequencer that runs entirely in the terminal.

I developed MusiCLI alongside David Ryan for [CornHacks 2021](https://cornhacks.com/), UNL's student-led hackathon.
For a hackathon project, I would say it turned out pretty good!
I wouldn't say this is anywhere near ready for "production" use, but the core functionality is there.

Currently, MusiCLI supports multiple channels, multiple instruments (including drums), and arbitrary-length songs.
The editor is fairly bare-bones for now, but it supports simple modal editing (via caps lock) and playing songs from within the editor.

Some major features we'd still like to add include loading MIDI files, playing individual notes as they're entered, and stepping through the song as it's played.
There are plenty of other convenient features we want to add too, but these represent the most significant technical hurdles.

To get MusiCLI, simply clone it from [GitHub](https://github.com/friedev/musicli), install the dependencies, and compile.
Note that MusiCLI has only been tested on Linux, and probably won't work on other operating systems.

MusiCLI is written in C++ and based on the great [Midifile](https://midifile.sapp.org/) library by Craig Sapp.
It is licensed under the GPL, and we're open to contributions via GitHub pull requests.
For more information, see the [project page](/musicli).

That's all for now, thanks for checking out this little project!
