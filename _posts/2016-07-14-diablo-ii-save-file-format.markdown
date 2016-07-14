---
published: true
title: Diablo II Save File Format
layout: post
---
I made a tool called [diablohud](https://github.com/krisives/diablohud) for streamers of Diablo II. In the process I had to piece together parts of documentation on the .d2s file format. From this I made the [d2s-format](https://github.com/krisives/d2s-format) specification to help anyone else interested.

Originally I found [GoMule](http://gomule.sourceforge.net/) but after reading the source they had some pretty nasty hacks to get around parts of the file they didn't understand. In particular I saw that they read item data they did understand and then scanned for the next `JM` header. Looking around at the various `.txt` files released in the MPQ of the game files I saw how they were connected and made a parser for that data.

The .d2s format requires working with data that isn't byte aligned, and because of this I had to roll a `BitBuffer` class that I will also be separating into a standalone library anyone is free to use.