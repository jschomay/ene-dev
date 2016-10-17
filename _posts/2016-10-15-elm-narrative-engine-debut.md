---
layout: post
title: The Elm Narrative Engine's Debut
---

[The Elm Narrative Engine](http://package.elm-lang.org/packages/jschomay/elm-narrative-engine/1.0.0) was born as a tool for creating and playing interactive stories that focus on dynamic narration and exploration over puzzle solving and branching choices, with a simple point-and-click interface.

I wanted to build it in [Elm](http://elm-lang.org/), and I was accepted as a speaker in the first ElmConf to present the story of its development.

I debuted the first [interactive story]({{ site.baseurl }}/sample-stories/curse-of-the-tech-demo/) exactly one month ago from when I am writing this, and am very happy that it was well-received.  Here is the video of the presentation:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/t8RSxzpw1Yw" frameborder="0" allowfullscreen></iframe>

<span></span>
<!--more-->

## Version 1.0.0

My initial intention was to have authors use my narrative engine by supplying a "story config" file written in Elm.  I tried to make it as simple as possible to describe the story world and story rules in a declarative, data-driven way, while still allowing for a very engaging and dynamic story.

I think I generally achieved that, especially with the declarative story rule builders.  Although I still had a list of improvements and ideas, version 1.0.0 was fully functional and fun to use.

{% highlight haskell %}
scene1rules =
    [ interactingWith (item Umbrella)
        `when` (unless (withItem Umbrella))
        `changesWorld` [ addInventory Umbrella ]
        `narrates` takingUmbrella
    , interactingWith (item Umbrella)
        `when` (inLocation Swamp)
        `changesWorld` [ ]
        `narrates` startingToRain
    ...
    ]

takingUmbrella =
    "Never leave home without it."

startingToRain =
    "Good thing your brought your umbrella..."
{% endhighlight %}

## Moving forward

I originally figured that what I had built for ElmConf would be about the extent of my plans.  With the framework "complete," I looked forward to using it to write many of my own stories that have been floating around my head.

However, I got a larger and more positive response than I expected, and the first inklings of where this project could go started to take form in many of the conversations I had with other developers in the community.

I anticipate bigger things coming soon for the "ENE."  I am actively developing it, and will continue the story with version 2.0.0.
