---
layout: post
title: Development continues
comments : true
---

I have not updated this development blog for a while, but that does not mean that this project is dormant.  On the contrary, I continue to work on new, exciting features, which make this engine more flexible and powerful than ever:

- Update the engine for Elm 0.19 - this has already been [released](https://package.elm-lang.org/packages/jschomay/elm-narrative-engine/3.0.1/).
- Remove all internal state from the engine, allowing it to work as a "plugin" rather than a "framework".  Coupled with the previous removal of the view and content layers, this continues the theme of allowing greater flexibility.
- Replace the hard-coded item/location/character categories with a totally flexible "salience-based" system.  This allows you to "tag" entities however you see fit.  You could add tags for "items", "locations" and "characters", but you could also work with "memories" or "families" or any kind of categorization you can come up with.  You can also create "links" to other entities for dynamic relationships.  (See Emily Short's blog post [Beyond Branching: Quality-Based, Salience-Based, and Waypoint Narrative Structures](https://emshort.blog/2016/04/12/beyond-branching-quality-based-and-salience-based-narrative-structures/) for more about this, and the point below.)
- Added a "quality-based" (or "stats") system to give you more control over building your rules, and to enable powerful structural patterns like "delayed branching".  (See more about this in [Choice of Games's article](https://www.choiceofgames.com/2011/07/by-the-numbers-how-to-write-a-long-interactive-novel-that-doesnt-suck/)).
- Working on a visual editor and new "query syntax" (something similar to CSS) to simplify authoring your manifest and rule sets, with the ability to see an immediate visualization of potential pathways through your rules, as well as preview the story with a debug mode.

At the moment, most of these features are in an internal testing phase, but I will report more as they get released, and if you are interested in experimenting with the latest features, feel free to reach out.
