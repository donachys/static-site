+++
date = "2018-04-15T00:00:00"
description = "Dragenvoy - Remixed for 2018 with Unity v2017.4.1"
thumbnail = "images/dragenvoy_ld26_2018.png"
image = "images/dragenvoy_ld26_2018.png"
title = "Dragenvoy - Remix 2018"
slug = "dragenvoy-ld-26-remix-2018"
author = "Shaun Donachy"
draft = false
hidesidebar = true
tags = ["Unity", "C#", "games", "gamejam", "2D"]
+++


### Nostalgia

Looking back over Dragenvoy from 2013 made me disappointed that the unity web player no longer works, and further that I couldn't simply export a new WebGL build with a more recent version of Unity. After getting a bit nostalgic I decided I'd like to give Ludum Dare 41 a crack as it is the 5 year anniversary since LD 26 when I made Dragenvoy. I figured it would be good practice to resurrect the old version (if I could.)

I wasn't sure how to proceed with getting a 5 year old project to work with today's Unity, but the first thing I knew I needed to do was rip out the 2d framework I was using. Suprisingly, after running Unity's project upgrade tools (after making a backup), then just completely deleting the 2d toolkit folder from my project everything compiled! Wow, I thought it would take much longer just to rip enough pieces out to get a compiling build. Well, let's see what happens when I run it, splash screen worked... good... but as soon as I started moving the dragenvoy everything went haywire. Clearly, the physics engine has changed a bit as well.

### Re-2D

Since Unity didn't support 2D back in April 2013 I was using another tool to help manage sprites and spritesheets. Rrrrrriiiiipppp ... took that out. All of my game objects were using custom components for managing sprites. I removed the components from all of my prefabs and the gameobjects that start in a blank level like walls and the background. Next, I needed to re-import all of my image assets as 2D sprites using Unity's importing dialogs and reassign them to their respective gameobjects and prefabs.

Unity now also supports 2D physics. Getting rid of that pesky third dimension prevents a whole class of mistakes that I made in my previous version. But now to make use of it I need to re-instrument all of my prefabs and gameobjects with the new components. Fortunately it wasn't too bad. I ran into one puzzling bug where my gameobjects were not reacting to collisions and flying across the screen as I wanted. Turns out this was just a matter of disabling the 'Is Trigger' checkbox on the appropriate gameobjects.

### WebGL works!

At this point I was actually able to start playing a bit. I tweaked a few aspects of the physics simulation and got rid of the pixelated green background to end up with 2018's remixed Dragenvoy. I recall when Unity started experimenting with WebGL back around 2013 and asm.js. I'm glad to see it has now become the standard, way to go! After going through this exercise re-familiarizing myself with unity, I feel better prepared and hope that I may actually end up with something playable after LD 41. Looking forward to the theme reveal on April 20th!

### Try it
Here is the link to [Dragenvoy - 2018](https://shaundonachy.com/dragenvoy2018/index.html).
