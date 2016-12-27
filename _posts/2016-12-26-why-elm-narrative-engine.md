---
layout: post
title: Why The Elm Narrative Engine?
comments : true
---

I recently contacted [Emily Short](https://emshort.blog/), the "Queen" of interactive fiction, to ask for some feedback on my new engine.  The engine was early in development, and she had some very good points that have led to important features.  But the most important question she asked me was, "Why are you making this engine?  What does it do that others don't?  Why is it special?"

Good question.  Let me share.
<!--more-->

## Why?

I am a screenwriter and programmer.  I have so many stories in my head that I want to tell in interesting interactive ways, but without losing focus on the story.  I want to be able to write these stories as I would a screenplay, by crafting dramatic arcs and varying the levels of tension, while still letting interactions drive the story forward.

I experimented with other tools, but felt compelled to make one of my own.


## A different approach

I modeled my engine not after other interactive fiction tools, but rather the old classic point-and-click adventure games, like Grim Fandango.  Instead of graphics I would have text, but the basic mechanics are the same -- you keep clicking on things until the next piece is revealed, and the story unfolds.

I simplified too, leaving behind clunky mechanics and distracting interfaces, like spatial navigation and object manipulation.  Instead of intricate exploration and meticulous puzzle solving, you would anticipate what happens next, planning your interactions by looking ahead.  My theory was that the simplicity of the mechanics would allow the story shine through -- for both the author and the player.

How is that different from other tools?  An unexpected early write-up in a blog post by ["No Time to Play"](https://no-time-to-play.tumblr.com/post/154410679767/user-interfaces-in-text-based-games) captures what the Elm Narrative Engine is all about pretty well.  It's not the verbs, its the nouns.  The nature and outcome of each interaction is determined by where you are in the story, and the pieces may respond differently at different times.


### A quick background on interactive fiction types

Interactive fiction breaks down into three basic categories:

1. **Parser** The original interactive fiction format, all about matching verbs with nouns to create meaningful results.  Examples include [Inform 7](http://inform7.com/), [Quest](http://textadventures.co.uk/quest) and to some degree [Texture](https://texturewriter.com/about).
2. **CYOA (choose your own adventure)**  Lets you choose a single path through a collection of intertwined branches.  Examples include [ChoiceScript](https://www.choiceofgames.com/make-your-own-games/choicescript-intro/), [Inklewriter](http://www.inklestudios.com/inklewriter/), and even [RenPy](https://www.renpy.org/).
3. **Hypertext**  Deals with jumping between "nodes" of text to piece together a larger context.  The most popular example is [Twine](http://twinery.org/).

Some of these approaches include a "world model" to represent the state of the story world (like which character is in which room and what they are holding, etc).  Some also track various "qualities" or "stats" as you progress, like how trustworthy or willing to take risks you are, which can affect future outcomes.

Each category lends itself to a particular kind of experience.  Parser games allow for rich, open worlds, and rich senses to explore them with and get lost in.  CYOA games let your choices move the story forward and define who you are.  Hypertext is especially good for more poetic pieces and a deep gestalt effect.  There are games in each category that stretch the format, but these usually require plenty of custom code.


### A "rules-based" approach

The Elm Narrative Engine doesn't fit directly into any of the categories above, though it shares qualities of each.  The primary system that powers the Elm Narrative Engine is a "rules-matching system."  The author creates rules where appropriate that match specific interactions and conditions to move the plot forward.  During game-play, for each interaction, the engine finds the best matching rule, and changes the world model as the rule specifies and delivers the associated story.  If no rules match, the player can move freely and inspect the surroundings, but the story will not advance.

This allows for a type of game with the narrative development of CYOA, but with a fuller and more open parser-like world offering the player a higher degree of agency.


### Architected for ultimate embeddability

Aside from the differences in approach and focus, the open architecture of the engine is a huge strength.  Unlike many other current tools, the engine (in the next release) totally separates the logic, content, and presentation of the game.  This allows for ultimate flexibility and integration.

Not only does this make aspects like custom layouts and designs possible, but it also opens the door to custom tooling and plugins, like a visual editor, story debugger, and dialog systems.


## Making it as simple as possible to tell stories that are as engaging as possible

I think I'm on to something here.  I want to make the Elm Narrative Engine great.  I intend to use it for my own stories, and want others to use it too.  I am working on making it more powerful and simpler to use.  You can [start using](https://github.com/jschomay/elm-interactive-story-starter) it today (though vast improvements are coming soon).  You can give feedback in the comments below, or even [contribute](https://github.com/jschomay/elm-narrative-engine).

Sign up for my [newsletter](http://eepurl.com/ckFcFD) to get updates on the next releases and the continuing development.
