+++
date = "2018-12-27T00:00:00"
description = "Multiplayer game using go and GRPC"
thumbnail = "images/cannon-go.png"
image = "images/cannon-go.png"
title = "Cannon-Go Battle"
slug = "cannon-battle-game-go-grpc"
author = "Shaun Donachy"
draft = false
hidesidebar = true
tags = ["golang", "GRPC", "go"]
+++

Designing games is immensely good fun. It's so much fun that I tend to bite off more than I can chew. Previously, I had chatted with [@rmbreak](https://github.com/rmbreak) about making a clone of the classic [gorillas](https://en.wikipedia.org/wiki/Gorillas_(video_game)) game where players throw explosive bananas at each other. One of the main features being that it is relatively simplistic and we might be able to get to a playable state quickly. Although that project has yet to materialize, the motivations for keeping things simple stuck around.

As a bit of history and some context; I've always wanted to make network-multiplayer games yet the prospect of building it seemed daunting. The build versus buy scenario comes up all the time in software development, and a memorable prior attempt at creating a multiplayer game was completely derailed after testing an off-the-shelf solution from Unity3d to find that it did not support the kind of multiplayer game I had in mind. The possibility of implementing the game server from scratch with no prior knowledge of remote procedure call networking seemed too tall of an order at the time.

### Game Design

The design is deliberately simple to keep the implementation manageable. It's a 2-player game where each player has a castle randomly placed on a field and a cannon randomly placed within the castle walls. Inspiration came from the [gorillas](https://en.wikipedia.org/wiki/Gorillas_(video_game)) game and the board game of [battleship](https://en.wikipedia.org/wiki/Battleship_(game)). Each player will be able to see the location of their opponent's castle as well as their own. But, the precise location of the cannon within their opponent's castle will remain hidden. The player's objective is to hit the opponent's cannon location. This may take many attempts because the player doesn't know exactly where their opponent's cannon is located. Each player's cannon may shoot once every three seconds and they modify their shot attempts by adjusting three parameters: power, rotation, and pitch.

### Server

I was interested in using a client-server architecture where the server maintains game state and validates client requests. The server was written in Go utilizing [GRPC](https://grpc.io) for communication between client and server. Implementing the GRPC server in golang is a relatively smooth experience. I got in some more solid practice with channels and found them to be a fantastic primitive for managing the complexity of concurrent programming, particularly for bi-directional streaming.

### Client

To simplify the client, and to experiment with the feasibility of terminal games I used the [termloop](https://github.com/JoelOtter/termloop) library based on [termbox](https://github.com/nsf/termbox-go) to implement the initial client as a terminal app. I'm grateful for the availability of termloop and termbox as it simplified the implementation and made it easy for me to keep everything in golang and in one repository.

### GRPC

The first step of setting up a game is implemented as a unary RPC call. Clients send a request to the server to signal the intent to queue for a game. The server is then responsible for matchmaking and game creation.  Once a game begins each player can send requests to fire their cannon independently, and their opponents must be notified immediately. Using the bidirectional streaming functionality built into GRPC therefore makes sense, and provides an opportunity for me to learn more about it!

### Challenges
##### Client Terminal UI
When building the client UI it quickly became clear that there were some UX issues. It was difficult to inform the player that their shot was off of the screen or that their shot did not fire because of the 3 second cooldown gated by the server. Implementing an animation for the player's shots would help alleviate the confusion. The server would need to be modified to send a remaining cooldown update to the client so the client could display it to the player. The number of input keys that termloop supports is somewhat limiting. I needed two inputs per firing parameter for a total of six, and then a fire command. I used up the arrow keys and spacebar and then I had to use a modifier key with the 'O' and 'P' characters for the final set of commands. Building UI's that work on a variety of resolutions is always a challenge, and the issue of handling different terminal window sizes remains to be solved on the terminal client. Termloop does provide the ability to specify an offset which would permit you to move the camera around. That would of course require additional keyboard inputs to implement.

##### GRPC
One confusing issue I ran into occurred when adding metadata to client requests. The error message I received did not directly inform me of the problem.

`failed.rpc error: code = Internal desc = stream terminated by RST_STREAM with error code: PROTOCOL_ERROR`

The issue turned out to be that when requesting input from the user a newline character was present at the end of the string. Newline characters cause this protocol error when added to metadata. So, the fix was simply to strip the newline character before adding it to metadata. I believe this issue still exists when targeting Windows.

Most of the time I have had no issues when using bi-directional streaming to play the game. On one or two occasions, though, I've had some unexpected interruptions. I have not yet determined how to properly maintain a long-lived streaming connection. I suspect I will need to implement a mechanism for retries and re-establishing a connection to a game. As of now the server just informs the clients when their opponent has disconnected.

##### Matchmaking
The matchmaking is extremely naive as I wanted to keep things simple. But I find the problem of creating matches to be fascinating. The various aspects of how to match players up so that the game experience is a positive one while also dealing with the technical implementation challenges could prove very interesting. I hope to revisit this problem in the future!

### Gitlab CI/CD
This was the first project where I used Gitlab's solution for automated builds. After a bit of ramping up on their build documentation I quickly got a working `.gitlab-ci.yml` working for an automated linux target test and build. I was able to use one of gitlab's provided regex's for golang to pick up the code-coverage value from the build output, but alas, it only reads the code-coverage value of the last module. Fortunately for me that module is 100% covered! 😅 It's also great that their system automatically keeps downloadable build artifacts around for you.

### Outro
I learned a lot and had a lot of fun working on this game so far. It definitely seems to me that GRPC is a viable communications tool for games, though I will need to figure out techniques to deal with interruptions to the stream. Terminal UI for games will continue to be a challenge I think. Even a basic game such as this one comes with challenges to achieve a reasonable user experience.

Since this game does not require a full simulation to run on the server and the client-server communication is relatively sparse, I don't see any issues with using a garbage-collected language like Go and the tcp-based GRPC protocol has worked well so far! I think it warrants further investigation.