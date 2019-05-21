---
layout: post
title: Spring Thing 2019 postmortem - finding hope in "Darkness"
comments : true
---

Two years ago I made a story game with the Elm Narrative Engine called ["Darkness"](https://www.springthing.net/2019/play_online/Darkness/index.html).  It was a small story, exploring some feelings around finding hope in dark times.  I also wanted to see if I could make a [Twine](https://twinery.org/)-like interface using my engine.  This is something the Elm Narrative Engine was never designed for, but given the engine's flexibility in the presentation layer, I thought it might be possible.

<!--more-->

The experiment mostly worked out, though not without issues.  My initial play-testers all had two similar comments -- first, that the UI was confusing, and second that the story was fairly flat and trite.  I tended to agree, so I hid the game away and didn't show it to anyone else.

Two years later, the game crossed my mind so I gave it another play.  It wasn't that bad.  It also was one of the more complete games made with my engine to date, and I felt bad keeping it hidden.  [Spring Thing](https://www.springthing.net/2019/play.html) was coming up, so I decided to showcase it.


## Reception

I don't know how many people played "Darkness," but I did get a handful of reviews.  Overall I was happy the impressions.  While they mostly mirrored the initial play-testers' critiques, they also revealed some genuine moments of joy, which is the best I could hope for.

### Story

As expected, I did get some criticism on the lack of depth in my story, setting, and characters.  However, I also received multiple unexpected praises on the feeling and tone of the story.  [bitterkarella](https://intfiction.org/t/spring-thing-impressions/41139) described it as a "tenuous dream logic feel," which I thought captured what I was going for better than I could have put it myself.

I was awarded the Audience Award for "Most Uplifting," which seemed very fitting for the theme I was exploring, so I was very pleased with that, and glad that I decided to share "Darkness."

One aspect of the story that I was particularly proud of, but didn't get many comments on, was some of the forking/looping I built in.  While there were only a few diverging paths, I felt that the way they looped back was very smooth, especially if you got the "negative" ending.


### Mechanics

The mechanics were both the most compelling, and most troublesome part of "Darkness."  This was a chance for me to show the flexibility of my engine, and surprise players with how it differed from Twine games.  Like Twine, I placed my interactive keywords directly in the prose.  But unlike Twine, these keywords could be used again, with different results, based on what happened before.  Players definitely seemed to enjoy discovering this aspect.  As [HanonO](https://intfiction.org/t/hanons-short-spring-thing-thoughts-in-progress/41063) aptly surmised, "I’m collecting an inventory of [re-usable] links Cool!"

The problem was in the UI.  While Twine is a web of interconnected text nodes, my engine models an ever-changing world, comprised of interactive entities.  Since the interface to these entities was embedded in the story text, as the story progressed, the interactive areas would scroll off screen.  This made for a lot of scrolling for the players.

Originally, I liked the idea of having players go back to faded-out paragraphs to search for keywords, as if stumbling around in the dark.  In practice, it was just annoying.  To help with this, I added a bar at the top that displayed all the available interactive keywords.  In an attempt to preserve some of the immersion of the experience, I had it auto-hide.  This turned out to be a very bad idea, as I got a lot of feedback about players "fighting with the UI."  I did actually update the game mid-festival to make the bar "sticky," but it was probably too late.  Unfortunately this UI problem detracted from the game in a pretty big way.

Another tactic I tried was to break the story up into different "scenes," which would clear the screen each time.  I struggled with how frequently I should clear the scenes.  Aside from an aesthetic standpoint, the tricky part was syncing visible interactive keywords with the state of the world.  For example, if I cleared the screen, the player could no longer interact with parts of the world that logically should still be present.  Or if an entity was removed from the story, but I did not clear the screen, I would have to ensure I had a rule to respond appropriately if the player click on the old keyword.

If I were to use this Twine style again, I would try to make it work a little more like Abigail Corfman's excellent [16 Ways to Kill a Vampire at McDonalds](http://www.abigailcorfman.com/Home/Vampire), which models a stateful world in Twine quite successfully.

One aspect of the UI that worked well was the "glow" effect on the text, and the way that background color would fade between black and white based on what was happening in the story.  I had a few reviewers comment on how it was slick and effective.  The inspiration for that came from Astrid Dalmady's neat nautical game [Tangaroa Deep](http://astriddalmady.com/deep.html).

As an experiment at emulating Twine, I think it worked rather well.  Choosing this game to demonstrate the Elm Narrative Engine may have backfired to some extent though -- I've noticed reviewers describing my engine as "Twine-like," which isn't quite accurate, given the differences in their approach, and the wide [variety of games](http://blog.elmnarrativeengine.com/sample-stories/#v3-demos) my engine can make.  Nonetheless, at least it is good exposure, and possibly has stirred up some interest.  I continue to work on the engine, and would be delighted to see others use it in future festivals!

Overall, I am very glad that I brought "Darkness" back to life and showed it off.  It may be flawed, but I learned to be proud of it.  I am happy that players found it uplifting, and it was fun being a part of the festival.

Thank you to everyone who played and to those who shared their feedback!
