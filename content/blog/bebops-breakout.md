+++
description = "Ludum Dare 41 Compo Entry"
date = "2018-04-23T00:00:00"
thumbnail = "bebopsbreakout/bebopsbreakout_cover.png"
image = "bebopsbreakout/bebopsbreakout_cover.png"
title = "Bebop's Breakout!"
slug = "bebops-breakout"
author = "Shaun Donachy"
draft = false
hidesidebar = true
tags = ["unity", "unity3D", "audacity", "C#", "gamejam", "Ludum Dare", "point-and-click", "text", "adventure"]
+++
### Building a game in 72 hours

A couple weeks ago after realizing (in shock) that it had been 5 years since my last GameJam, I decided to commit to [LD41](https://ldjam.com/events/ludum-dare/41/). For the uninitiated, GameJams are like hackathons for video games where you build a video game over the course of a weekend. [Ludum Dare](https://ldjam.com/about) is one of the largest GameJams and it is run 3 times per year by the awesome [@pov Mike](https://ldjam.com/users/pov). I successfully recruited two brave first-time game-jammers willing to sacrifice many hours of their weekend to join me on this epic journey: [@soylalluvia](https://ldjam.com/users/soylalluvia) [@alexis-vana](https://ldjam.com/users/alexis-vana).

### Prep work

Well it had been 5 years since I had opened Unity3D; so I knew lots of things would be different. Fortunately, though, many things were still the same. I just needed to jog my memory a bit on all the little gotchas Unity throws at you. I set out to update my 5-year-old GameJam game [dragenvoy](https://shaundonachy.com/projects/dragenvoy-ld-26-remix-2018/) since it no longer builds in Unity 5+. You can play the remixed version [here](https://shaundonachy.com/dragenvoy2018/). There were many improvements made to the 2D system which I knew we would be able to leverage for LD41.

In addition to that [@soylalluvia](https://ldjam.com/users/soylalluvia) did a little intro on point-and-click adventure games which I'm pretty sure I had not played since King's Quest V. I was also interested in a story-driven type of game, so it seemed like a good genre to pursue for a GameJam game.

### The Theme!

I participated as the pool of themes narrowed from over 3000 down to the final pool of 16 themes.
Here's what my final vote looked like:
![final_vote](/bebopsbreakout/final_themes_ld41.png)

Discussing these during the voting with my teammates and other folks, I predicted that the theme of "Combine 2 incompatible genres" was likely to win. It just seemed like so many hilarious combinations would be created if that were the theme. We eagerly awaited the announcement of the theme on Friday evening. We were inspired by the great keynote if you want to check it out:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/TjuZvDYqcRs?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Turns out my prediction was right, the theme was:
"Combine 2 incompatible genres (e.g. turn based racing)"

As pointed out by the [news post](https://ldjam.com/events/ludum-dare/41/$73264/ld41s-theme-combine-2-incompatible-genres), the theme did not specify "Video Game" genres, but just genres in general, so this could be music genres, book genres, etc. I was excited for what we could come up with. We had some hilarious ideas that were kind of all-over-the-place. Admittedly, I was biased towards combining incompatible video game genres.

### Selecting the premise and Designing the game

It helped us to narrow it down to one game genre that we were already excited about: point-and-click adventure games! So we started there and we thought about what such a game combined with other genres would be like. We also knew we wanted to stick with 2D as none of the team members had any experience with 3D tools. We hit on the idea of a text-based rpg/adventure game mixed with the point-and-click adventure game and everyone found the idea hilarious in a [QWOP](http://foddy.net/Athletics.html?webgl=true)-like way. Inflicting pain on the players in a ridiculous way got us all laughing and we were encouraged by our honorary team member Richimus. We brainstormed on what the interface would look like and what kinds of commands we would permit. We laughed a lot about making the commands and any names or interactables in the game as long as possible. A command like "give" would become "bequeath" and we could incorporate extremely long words like sesquipedalianism itself as the tendency to use long words.

### Story

[@soylalluvia](https://ldjam.com/users/soylalluvia) was the driver of the development of the story. The [Coachella](http://coachella.com) festival was happening near LA this past weekend, and good 'ol Beyonce was performing there. Wouldn't it be ridiculous if there was a cat at such a music festival? 🤔 Not just any cat... but a magical floating cat. Stuck there by the will of their human. Wouldn't you know that magic cats simply abhor pop music, but are big fans of the completely incompatible jazz genre. Big thanks to [@soylalluvia](https://ldjam.com/users/soylalluvia) for designing the game and driving the story.

### Adventure games

I had never attempted to implement an adventure game before. Completely re-learning Unity and coming up with a system to implement an adventure game turned out to be quite a challenge. Unity offers some tutorials, one of which is an adventure game tutorial. I took some cues from their system and implemented a similar "Conditions" and "Reactions" system along with an "Inventory" system. The final version of the framework could be greatly improved in many dimensions but I am happiest with the fact that there are few major game-breaking bugs that would allow players to perform unintended actions or get themselves completely stuck.

It would be interesting to develop this concept further, possibly in another game engine entirely, or by integrating with the Unity editor and enabling more types of conditions and reactions, in a greater variety of scenarios.

### Submission time

We managed to find some time just before the deadline to work in some more voices and sound effects. I think these went a long way to improving the functionality of the game and helped to explain the story. The voiceovers were a lot of fun and turned out reasonably well. But why does Bebop the cat have a scottish accent? who knows...
The final 20 minutes before submissions closed were extremely hectic. We managed to get the build on [itch.io](https://donshinski.itch.io/bebops-breakout), source on [GitHub](https://github.com/donachys/bebopsbreakout) and the description written and posted on [ldjam.com](https://ldjam.com/events/ludum-dare/41/bebops-breakout) along with screenshots. Phew! that was intense. Afterwards I was completely drained mentally. I feel that my brain was barely working at that point!

### Retro

It's always good to take a look back at the experience. I was reminded once again how frustrating developing with Unity can be. We tried out the (new to me) feature for collaboration on a project. When it worked, it was fantastic. But when it doesn't work 100% you can't rely on it, and that creates frustration and time spent working around it is lost. I would really enjoy having a better alternative that provides some of the great features Unity provides (cross-platform support, WebGL builds, built-in systems like physics, UI, and sprites... and many more) with a framework that was friendlier to programmers. I definitely underestimated how difficult it would be to have a framework for defining the interactions a player could perform, and also how defining those interactions would go. Maybe a better-planned framework could help there. Audacity performed admirably, but [@soylalluvia](https://ldjam.com/users/soylalluvia) definitely had some gripes about the effiency of Adobe Edge Animate. Having never used it, itch.io turned out to be a good hosting site that made it simple to upload our game at crunch-time. I also have a non-embedded version you can play [here](https://shaundonachy.com/bebopsbreakout/). Try it out!

### Rating

Wow this is the fun part. So many great games. There were 2346 Games submitted for LD 26 and there were over 3000 submitted for LD 41. I will unfortunately never see them all, but the ones I have tried have all been fantastic. I'll have to keep practicing if I want to be able to keep up with them. Maybe I can try out some of the other final themes that didn't get selected! So, thanks to everyone for rating our game, thanks to my teammates for an awesome jam, and I can't wait for the next one. Cheers!

### Spoilers

<div id="spoiler" style="display:none">

<h1>Bebops breakout walkthrough!</h1>

After the intro, Bebop starts on the left side of the tent. You must use the on-screen keyboard to type the commands.

<pre><code>look</code></pre> and Bebop will complain about the music.

<pre><code>float left</code></pre> and Bebop gets scolded by his human.

<pre><code>float right</code></pre> and Bebop moves to the middle of the tent near his human.

<pre><code>grab</code></pre> to make London La Croix drop her kombucha.

<pre><code>float right</code></pre> to move Bebop to the right side of the tent near the suspicious table of pills.

<pre><code>grab</code></pre> to grab the pills and place them in Bebop's inventory.

<pre><code>float left</code></pre> and Bebop moves back to the center of the tent.

<pre><code>interact</code></pre> and Bebop identifies the kombucha. <pre><code>look kombucha</code></pre> also provides a clue here.

<pre><code>interact kombucha</code></pre> to put the pills in London La Croix's drink. She will then depart.

<pre><code>float left</code></pre> to go to the left side of the tent.

<pre><code>float left</code></pre> to exit the tent.

Congratulations, you're on your way to freedom floating past those crop-top kitty groupies. Cheers!

</div>
<button title="Click to show/hide content" type="button" onclick="if(document.getElementById('spoiler') .style.display=='none') {document.getElementById('spoiler') .style.display=''}else{document.getElementById('spoiler') .style.display='none'}">show/hide</button>