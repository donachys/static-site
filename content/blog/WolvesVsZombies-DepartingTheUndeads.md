+++
date = "2023-12-04T00:00:00"
description = "Wolves vs. Zombies: Departing the Undeads"
thumbnail = "images/wvz-dtu-1920x1080.png"
image = "images/wvz-dtu-1920x1080.png"
title = "Wolves vs Zombies"
slug = "wolves-vs-zombies-2023"
author = "Shaun Donachy"
draft = false
hidesidebar = true
tags = ["Godot", "godot4", "C#", ".Net", "games", "2D", "shmup"]
+++
### Departing the Undeads

Wolves vs. Zombies is a shoot'em'up (shmup) where the player must pilot their aircraft and guide their fellow villagers to safety. The autogyro-style aircraft fires forward giving the player a way to remove undead obstacles and rescue the villagers from a frightful fate.

<center><video controls><source src="../../mov/L4gameplay_480p.mp4"  controlsList="nodownload" preload="metadata" poster="../../mov/lv4_cover_480p.png" type="video/mp4" loop=false></video></center>

### Project goals
There were a few overlapping priorities for developing this game. The first priority was reaching something resembling a completed game. This goal is about learning and practice and differentiates the game from the prototype and gamejam projects I have developed previously. Second, I wanted to make a deliberate effort to step outside my comfort zone and level up in areas of game development other than programming and game design; areas that I am more familiar with.

I chose a simple game genre that I was confident would be light on game mechanics and programming and began developing.

### Open source and tools
Where possible I tried to stick with free and open source software (FOSS). Some of the tools I ended up learning and using the most:
* [Godot game engine (v4.1)](https://godotengine.org/)
* [Inkscape](https://inkscape.org/)
* [GIMP (GNU image manipulation program)](https://www.gimp.org/)
* [Beepbox](https://beepbox.co)
* [jsfxr](https://sfxr.me/)
* [Audacity](https://www.audacityteam.org/)

### Issues
With any project it is reasonable to expect to encounter some difficulties, and this game proved no exception. Although many more were encountered, I will only discuss a few issues that resulted in a significant loss of time and affected the final game result.

#### 2D skeleton animation in Godot 4.1.1
My first clue that something was awry was when I worked through the godot tutorial for [cutout animation](https://docs.godotengine.org/en/4.1/tutorials/animation/cutout_animation.html) and [2D skeletons](https://docs.godotengine.org/en/4.1/tutorials/animation/2d_skeletons.html) and some of the features were no longer available. To be fair, the page does give a warning that the page was not up to date for 4.1. That said, many of the docs pages have similar warnings but go on to have accurate information.

I found some more up to date information from videos and actually got 2D skeleton animation to work within the editor using the [SkeletonModificationStack2D](https://docs.godotengine.org/en/4.1/classes/class_skeletonmodificationstack2d.html) property of a 2D skeleton, albeit with numerous warnings that seemed to be erroneous. I proceeded to iterate and animate until I was ready to start adding characters to a test scene, which worked fine until later when I added a second instance of the character scene. Sadly, this seems to be completely broken causing the animations to fail, and the game and editor to crash. I ended up dropping the animations entirely.

<div class="image centered"><image stile="cursor:pointer;" title="Errors go Brrrrrrrrr..." src="../../images/errs_90x160.gif"></image></div>

One possible workaround would be to take screenshots or export images of the animation and use a fully sprite-based animation. I would say this is the most problematic issue I faced with Godot engine, which I intend to be a compliment! I have enjoyed working with Godot so far and I'm excited to continue doing so in the future.

#### Collision detection
Collision events can be connected from `Area2D` as well as using `MoveAndSlide` or `MoveAndCollide` methods of a `CharacterBody2D` or `RigidBody2D`. Certain combinations do not play nicely together, causing me to trial and error my way into finding what worked. The result was a lot of gnarly code and nodes with both collidable areas and bodies. For future projects I'll be sure to lay out these combinations in advance to come up with a suitable system to handle collisions. Using the `MoveAndSlide/Collide` methods only seem to detect collisions on the body that is moving towards the other body. So, if one body is moving away at a slower rate than the incoming body that is moving faster. Only the faster moving body will detect the collision. I do not have a satisfactory solution to this problem. My best guess at a workaround would be to have a class that can receive these events and dedupe them for the case where each body detected a collision but also handle event distribution for cases where the collision was detected by only one body.

#### Runtime crash
Perhaps this is attributable to the relatively new feature of C#/.Net support in Godot 4, but I have observed intermittent runtime crashes. The crashes appear to be part of the .Net runtime and unrelated to the game code. Further investigation would be necessary for a more robust game release and this issue is worrisome for choosing to go with Godot as the game engine.

### The results are in

Well, how do I think it turned out with respect to the projects' goals? I'd give it a definite 'pretty alright' rating 😂. WvZ:DtU is the most complete game I've made. So, on goal number one I consider it a success. Goal number two I also consider a success. I gained a lot of knowledge in areas I had little prior experience in.

#### Audio: music and effects
I created a bit of music for this project: something I have not gotten very far with in the past. I found beepbox to be a great tool for me. Along with the great, [How to make a music video](https://www.youtube.com/watch?v=QP6QFV1wqDY)! Beepbox is simple yet provides enough features to create _something_ and then listen, iterate, and repeat. It also helped me learn a bit more about music theory. I created original tunes as well as transcribed sheet music and landed on results I was content with.

Sound effects are quite challenging to create from scratch. Both beepbox and jsfxr found use for this task, but ultimately I ended up needing some external assistance. I used some audio effect assets I had picked up previously and they came in handy for gameplay as well as UI audio cues.

#### Visual arts: illustration and animation
I improved my skills with vector graphics and inkscape by orders of magnitude during the development of this game. I found that it may be within reach to create passable vector graphics and cutout animations with some more work. I also got a much better grasp on the time/effort necessary to produce each asset or character. I am more or less very pleased with the results in this area, though I had to make concessions for the sake of time. I'd like to better understand achieving a consistent art style for a game's assets.

#### User interface design
I found this area to be quite challenging, though I did make some meager skill improvements. I did not spend nearly as much time on this as I would have liked. When it comes to programming UI with the godot engine I did greatly improve my knowledge and have some examples to derive from in future projects. Godot offers some useful options for handling multiple resolutions that are capable of scaling the viewport(s) in various ways. I was able to apply these settings without many changes. It was definitely a productivity boost compared to making multiple versions of every asset.

#### Project management?
This topic probably doesn't come up as often for game development, but given that game development involves so many different domains and the details really matter, I find that project management is a very important aspect to a game development project's success. I would say I have yet to encounter a truly amazing solution, but I found a system that works for me. It's flexible enough to permit handling of ad-hoc tasks and high-level enough to prevent process from getting in the way of productivity. For the duration of this project I used [Notion](https://notion.so) for keeping project information, details, and tasks organized and synced across devices. It's worked out well, and I will continue iterating on this approach.

### Try it
<iframe frameborder="0" src="https://itch.io/embed/2406426?border_width=2&&" width="554" height="169"><a href="https://donshinski.itch.io/wolves-vs-zombies-departing-the-undeads">Wolves vs. Zombies: Departing the Undeads by don.shinski</a></iframe>
