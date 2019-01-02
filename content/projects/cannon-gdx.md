+++
date = "2019-01-01T00:00:00"
description = "Multiplayer game using libGDX and GRPC"
thumbnail = "images/cannongdx.png"
image = "images/cannongdx.png"
title = "Cannon-GDX Battle"
slug = "cannon-battle-game-libgdx-grpc"
author = "Shaun Donachy"
draft = false
hidesidebar = true
tags = ["java", "libGDX", "GRPC", "game", "multiplayer"]
+++

The [libGDX](https://libgdx.badlogicgames.com/index.html) project hosted [on github](https://github.com/libgdx/libgdx/) has come a long way since I first encountered it during a gamejam in 2013. Multiple platforms including mobile and desktop are supported and the feature set is great! I wanted to try it out and see if it might be a good choice for me to use during game jams and future game projects. Since Java is a fully-supported language for [GRPC](https://grpc.io), I could use libGDX and GRPC to build a client for [cannon-go](https://shaundonachy.com/projects/cannon-battle-game-go-grpc/).

### Getting started

I took my first steps with libGDX and used the handy [project setup tool](https://libgdx.badlogicgames.com/documentation/gettingstarted/Creating%20Projects.html) and started bringing in some of the example code from [libgdx.info](http://libgdx.info/). ([External tutorials](https://github.com/libgdx/libgdx/wiki/External-tutorials) are also a great resource I encountered later.) After I was confident that I could implement the features for a GUI to support Cannon-GDX I just needed to see about adding GRPC support to the project. Although libGDX provides gradle scaffolding, and the GRPC documentation also has a gradle build example, they had different approaches. The libGDX starting gradle setup supports building to multiple targets, a nice feature. The GRPC example did not have such a setup, so being completely new to gradle I had some difficulty integrating GRPC into the project. After a _lot_ of trial and error and juggling different versions of gradle plugins and protobuf plugins I finally got to a gradle setup that would compile the `.proto` files and put the generated output on the classpath. I'm certain that gradle wouldn't be so mystical if I was more familiar with it, but is significantly more complex than the couple lines in a makefile that the [cannon-go](https://gitlab.com/donachys/cannon-go) project uses. Alright! so I got my feet wet and I know how to include GRPC classes, time to create the base project and get started!

### Game setup screen

The first step a player must complete is putting in their name and connecting to the game server. For this step a unary synchronous GRPC call is all that is needed. Not too much trouble setting that up, but it quickly became clear that GRPC in java is very different than using GRPC with go. The builder pattern is used to construct all of the classes which are derived from the `.proto` file; not too bad once I became familiar with it. With that setup and working the next step is moving to a pre-game screen.

### Pre-game screen

This screen just has a button for the player to indicate they are ready to start the game. But to do so, we have to get the bi-directional streaming connection set up. This part started to get tricky as I needed to become familiar with how GRPC and java handle asynchronous calls and concurrency. The client sends and receives data asynchronously and a lock is used to prevent concurrent access to some of the game state information.

### Game screen

Now that the bi-directional stream is established, the player's have both indicated they are ready, the game can begin!
One challenge I ran into was how to deal with creating OpenGL textures based on an asynchronous receive from the server while the UI thread was the only thread with access to the OpenGL context. When the game is created many of the textures are already loaded and we just signal that they may be displayed and adjust the gamestate for where to display them. A big improvement over the terminal client comes from being able to see which direction your cannon is rotated and watch your opponent's shots come in. The parameter ranges needed to be restricted to more reasonable values so the slider inputs would permit the kind of fine tuning needed to adjust the cannon's aim.

### Important libGDX concepts

As I developed the game client there were two important concepts I encountered: scene2d UI tables and GDX screens. Screens share some similarities with scenes in the [Unity Engine](https://unity3d.com) and the UI tables come in very handy for laying out UI elements on a screen that can vary in aspect ratio and resolution. Getting the tables to perform exactly how I would like is still a work-in-progress. It took some trial and error to get the game-setup screen laid out similar to what I had in mind, but I think the result is worth the effort in understanding the layout system.

### Iteration

My first complete implementation used placeholder assets and functioned much like the terminal client. The GDX client had the same poor UX of the terminal client. This was a good opportunity to learn how libGDX handles animation. I implemented some animations to show the cannonballs trajectory and landing point. Since showing the origination point of the opposing player's shots would give away their location, enemy shots just drop straight down from above. The inability to see which direction your cannon is facing was fixed by having the cannon sprite rotate around to point in the direction it's aiming. These two improvements made the UX much better.

I then replaced the default skin that I was using from tutorials with the holo skin; one of the freely available skins available [here](https://github.com/czyzby/gdx-skins). The skin system is a nice feature, it made swapping out the stylings of the UI elements fairly straight forward.

One final improvement over the terminal UI is the restriction of the parameter ranges to ease the use of the UI sliders. The rotation is restricted to a 90 degree range aimed at the center of the opponent's base. The power and pitch ranges are restricted to static values that permit the player to target the opposing base without excess.

### Ready to play

Now it's possible to play with either of the two clients! One player can use the terminal client in the [cannon-go](https://shaundonachy.com/projects/cannon-battle-game-go-grpc/) repository and the other can use the libGDX GUI client! I updated the placeholder game assets to use textures that I created with Illustrator and Photoshop. Utilizing GRPC enabled the clients to communicate with the server in an indistinguishable fashion from the server's perspective. Implementing this second client helped improve the server and brought some new and interesting challenges and opportunities for improvement.

Two areas I'm interested in exploring is making a computer-controlled player (a bot) for the players to play against. It will require some careful balancing between being too good and an interesting challenge. The second area I'm curious about is improving the matchmaking, and moving it to a separate grpc service that the game server can communicate with.
I've enjoyed the chance to use some new tools and learn more about libGDX while having some fun building a new client. I'm pleased with the result! You can see an animated demo of the gameplay below or check it out on gitlab!

<div style="text-align:center;"><img src="../../images/cannongdxdemo.gif"></img></div>

The source code is hosted [on gitlab](https://gitlab.com/donachys/cannon-gdx)
