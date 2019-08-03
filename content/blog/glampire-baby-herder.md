+++
description = "Ludum Dare 44 Compo Entry"
date = "2019-05-01T00:00:00"
thumbnail = "glampirebabyherder/glampire_cover.png"
image = "glampirebabyherder/glampire_cover.png"
title = "Glampire Baby Herder!"
slug = "glampire-baby-herder"
author = "Shaun Donachy"
draft = false
hidesidebar = true
tags = ["unity", "unity3D", "audacity", "C#", "gamejam", "Ludum Dare", "top-down", "2D", "adventure", "your life is currency"]
+++
### Ludum Dare 44!

Two more Ludum Dare gamejams passed which I was unable to participate in. When the third one rolled around and I realized another year had gone by I thought about entering but wasn't very serious about it. That's when [@mackcam](https://ldjam.com/users/mackcam) got in touch about working together for the gamejam. Heck yea, I was in for [LD44](https://ldjam.com/events/ludum-dare/44/)! I figured this time I would keep a pretty casual attitude about completing our submission.

### Prep work? what prep work

The gamejam preparation was quite light 😅. I ran through a tilemap tutorial and declared myself competent, haha!
I had used Unity recently enough to feel comfortable with the editor and writing my game scripts in C#.

### The Theme!

I followed along from the early rounds of voting and even contributed my own for the first time. Sadly, none of my contributions made it beyond the theme slaughter round. Incredulous! Oh, well. As usual, watching the keynote is always a good way to get into the mood while waiting for the theme announcement. Here it is...

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/bdq-IYxhByw?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

The theme was announced on twitter as **"Your life is currency"**

Darn! This is one theme from the final voting list that I had specifically mentioned to [@mackcam](https://ldjam.com/users/mackcam) I would prefer not to see chosen. I think the best themes are widely interpretable, but I feel this theme has one interpretation and its entirely _literal_. The example I first think of is the feature in Binding of Isaac in which you sell your hearts for an item.

### Selecting the premise and Designing the game

With a few gamejams under my belt I felt confident suggesting to my colleague that whatever we decide to pursue at the beginning will be completely different than our submission 😅. (Spoilers! This prediction turned out to be accurate). This was also my first jam working with a remote team member, so we had to figure out how to make that work for us. We hopped on a call at the beginning to discuss ideas, then took a break to brainstorm and reconvene later. These periodic check-ins worked well for us and slack was an effective tool.

For myself (and evidently other gamejam entrants), thinking about life as some kind of transferrable currency tended to make me think about vampires; blood and life. We tended to discuss the theme as if the involvement of vampires was a foregone conclusion! Along with vampires, babies, being the dawn of new life, were also frequently in discussion around the theme between [@mackcam](https://ldjam.com/users/mackcam) and I. It was these ideas that hid in the back of our minds which turned out to be important influences in what our submission would become.

I worked on generating creative interpretations of the words in the theme. Currency can be interpreted as "staying current" and instead of treating life as _health points_ there are other ways to look at it... the lives of individuals or perhaps lives that one may call their own. We pursued an interpretation of the theme based on today's _influencer_ occupation. The lives of these individuals are put on display and monetized directly as currency. Perhaps we could have the players exploring the game world while making choices, building their brand with social media posts and, of course, selfies. Gaining followers along the way to earn points and eventually culminating in acquiring sponsorship to validate their status as _influencer_. If there isn't an influencer simulation game out there yet, I'm pretty sure there will be one coming! Seems like a dream job for a lot of folks.

Implementing all of those features seemed a bit too ambitious for a game jam, so we wanted to adapt the idea. We landed on a concept where the player would be unable to control their transformation between human, vampire, and bat forms.  Being committed to the life of an influencer but being unable to tell the world about their shape-changing condition puts players in a humorous situation. They would have to maintain multiple separate influencer personas and each audience would be interested in different content. The players would need to choose their actions wisely to keep their follower counts up. Each form would have an advantage (movement speed for the bat, ability to consume humans as a vampire, etc.) and the actions players took would affect their follower counts on each of the respective accounts.

### Development

We began implementing components of the shape-changing influencer game but ran into some issues clarifying the design. Some of the details were intentionally left vague to be further defined later. If we had proceeded further with some of the details it would have been clear that we had a game that was too large in scope or just un-playable. We did make some progress putting together some tilemaps and a vampire character, lovingly named Vampy, using sprite sheets that were available on [opengameart](https://opengameart.org) to begin testing out ideas.

With our casual attitude towards this gamejam and the underwhelming theme we hadn't made too much progress by Sunday evening (about 48 hours in). I began to despair, but decided to press onwards with the content we already had and change the design to something we might be able to submit with the remaining time. This is the point where what would eventually become **[Glampire Baby Herder](https://ldjam.com/events/ludum-dare/44/glampire-baby-herder)** begins to take shape!

During the phase of development where we were creating components but had yet to determine what they would eventually become I had jokingly created a sprite (also from [opengameart](https://opengameart.org)) of a crawling baby to use as a placeholder, but due to the time pressure I decided to roll with it and keep the bebes! So that's how we ended up with vampires and crawling bebes 🤔. I also needed to simplify the game to have a chance at finishing in time so... The design was changed from the influencer-simulation game to a more literal theme interpretation. Using the more obvious theme interpretation meant I would have less work explaining the theme's relevance to the unfortunate souls who would eventually play this game.

In this topsy-turvy mixed up world vampires feed off of gold instead of the usual blood-food of those cliché vampire stories. As it turns out the bebes are actually dwarf bebes! Who knew? The dwarves are hardy folk and prefer to let their bebes roam freely to build up their strength and courage. The vampires of this land offer a bebe return service in exchange for gold. A fine symbiotic relationship. Of course, there are some dwarves who prefer the vampires not to mingle among the dwarf villagers and especially their bebes, so they **rob** them of their hard-earned gold! Poor Vampy, what a tough world.

So, we have a game where players run around collecting the roaming bebes and turning them in to the inn for cash. The catch is that finding and returning the bebes uses up Vampy's energy and the players must eat their gold to replenish energy. Taxes raise each round and Vampy will inevitably be unable to keep up with the cost of living... and perish. To defend himself against the vigilantes Vampy can also pick up axes and throw them at the dwarven robbers. With these mechanics decided, it was a matter of implementation and filling out the map.

### Submission time

Much like [Bebop's breakout](https://shaundonachy.com/bebopsbreakout/), the audio was the final addition to the game. It was a mad dash to the finish line, and once again the sound made a huge difference in the final game. I regretted opting out of the sound category for LD 41 because the character voices were all original and decided I would not opt out for LD 44. I was completely cooked after furiously working to get something that was submittable within the time limit and the submission page suffered, unfortunately. I probably could have improved it after the submission, with screenshots or gifs and better instructions, but I spent my time trying out everyone else's games instead!

### Retro and feedback

My experience with Ludum dare events suggests they are effective at encouraging participants to give insightful feedback to their fellow gamejammers using their coolness-factor metric. Everyone is always supportive and I think that keeps myself and others coming back to participate.

LD 44 was no different! I had a lot of very good feedback about the (mostly known) issues that the game has. I was still very grateful that people took the time to play and rate my submission. I even received helpful tips for fixing some graphics issues that I wasn't sure how to solve myself. Many twitch streamers will host streams and accept signups from folks who made a submission. I encourage everyone who participates to try and get someone to play their game on-stream. Having the opportunity to watch a player go through your submission page to playing through your game is such valuable feedback! This time [@mrjoshuamclean](https://ldjam.com/users/mrjoshuamclean) played my game [on stream](https://www.twitch.tv/videos/427560061?t=02h30m42s) and I sincerely appreciate the feedback!


### Results

After a few weeks of rating games, I was excited to see the results but expected fairly low scores given how the event worked out for me and [@mackcam](https://ldjam.com/users/mackcam). Here they are!

```
Final results
Overall: 919th (3.025 average from 22 ratings)
Fun: 996th (2.7 average from 22 ratings)
Innovation: 515th (3.15 average from 22 ratings)
Theme: 428th (3.5 average from 22 ratings)
Audio: 406th (3.25 average from 22 ratings)
Humor: 71st (3.881 average from 23 ratings)
Mood: 824th (2.95 average from 22 ratings)
```
\
Our game did ok; landing somewhere in the middle overall, a pretty good result considering our circumstances. I was extremely pleased to see that the humorous aspects were well received by the raters, wow! First time breaking the top 100 in a category, that's a great result for me. I think the silliness of the game worked well with the sound effects to help us out in the `Humor` category. Lesson learned; I think I should spend more time on audio in future submissions.

Much thanks to the organizers of Ludum Dare for putting on another great gamejam event! Cheers!


A playable version is [here](https://shaundonachy.com/glampirebabyherder/).

LD44 Submission page [here](https://ldjam.com/events/ludum-dare/44/glampire-baby-herder).
