---
layout: post
title: Writing Twine-style fiction in the Elm Narrative Engine
comments : true
---

[Twine](https://twinery.org/) is one of the more popular tools for writing interactive fiction.  Specifically, Twine stories are "hypertext" fiction, meaning certain words in a node of text can "jump" you to a new node of text, allowing for non-linear exploration of different contexts.  Often, these allow the reader to create a narrative unique to the paths they choose to explore.  Other times, hypertext stories provide an exploration of a topic from multiple facets, rather than a traditional plot.  In general, Twine stories offer limited customization, relying on custom scripts to do anything beyond the "jumping" behavior.


## Attempting Hypertext in the Elm Narrative Engine

The release of [version 3 ( NEEDS LINK )]() of my engine brings a complete separation of logic, content, and presentation.  This separation allows for profound customization.  As a test of this separation, I attempted to create a hypertext-style story, something that the engine was never designed for.

I created a story called ["Darkness" (NEEDS LINK)](), a fable about bringing light into the world through our interactions with other people.  I wanted a very simple and elegant look, playing with the themes of darkness and light, and I wanted it to feel like a Twine game with branching narratives, but with a stronger plot arc.

![Darkness screenshot]()

<!--more-->

### Writing the story

The presentation is extremely simple, just text on a solid background, however, the colors of the text and the background animate between black and white dynamically based on what is happening in the story.  The "HUD" of the classic theme, like the inventory list and current location information is removed, leaving only the narrative.

The content layer gains a whole new feature through the use of a custom "hypertext plug-in" (or "component" in the new [entity-component-system architecture of v3 (NEEDS LINK)]()).  This allows me to write narrative content like `I am alone in the [darkness]`,  and the word "darkness" will be parsed in the view into a clickable word representing the "darkness" location.  Clicking on this word will trigger the normal rules system to progress the story.  All this works without any changes to the engine.

Putting this power at the content level has interesting consequences.  The engine still has a world model, however, instead of rendering it out in the view, the content that you provide must explicitly include any parts of the world model that you want to be intractable.  And likewise, if a part of the world model is removed, such as a character leaving, the existing text still remains (unless you switch scenes), requiring story rules to provide an appropriate response for all visible clickable words at all times.

Additionally, there is no requirement for the world model and text to be in sync, though the rules system only responds to the world model, so you have to be careful of story bugs.  However, you get the option to "render" the world how ever you like, when ever you like.  For example, the parsing allows a syntax like `I am alone in the [darkness|ever present suffocating emptiness]` if you would like something more poetic than the id for darkness to be printed.  Also, you don't have to reveal  something even if it is in the world model.  This can be useful to make complex rules work without adding "noise" to your story.  Another interesting technique which is not possible in the vanilla engine is delaying rendering an interactive part of the world model by putting it later in a cycling narration.  This way, the player would only see it after interacting with the same thing more than once.  All of this allows for more freedom in creating the text of story.


### Not Twine

Although stories like "Darkness" look and feel like Twine, they have some significant differences.  Aside from the tooling, the biggest difference is mechanics.  As mentioned, Twine does not have a world model by default, while stories on my engine always progress through the same context sensitive rule-matching mechanics.  This means that clickable words may do different things depending on the current context of the story world and the history of interactions.  Furthermore, going back to a word that you have already clicked on may have a different reaction than the first time you clicked it.  This allows for deeper texture, more control over plot, more control over game/puzzle mechanics, and more dynamic story-branching options.

As one of my test players remarked, "I've never seen a Twine do that."


### Challenges

Making this test of the new engine did come with some challenges, primarily in the UI/UX.  The main obstacle was the fact that words would stay on the screen, and thus needed to always have appropriate rules tied to them.  At first I had the system clear the screen with every interaction, but this lead to a less interactive experience, essentially giving the player nothing more than a fancy "next" button.  Similarly, not clearing the screen at all made for cases where every interactive word that was ever rendered stayed "active," even if it didn't make sense.  I settled on clearing the screen every "scene change," and making sure my scenes were well contained, and had rules to cover any interactive word that could be rendered during that scene.  Luckily, this is what the engine's rule system is very good at.

Another challenge was the problem of scrolling.  Because words near the top of the scene might be needed later in the scene, gameplay involved a lot of scrolling.  This was annoying, especially on mobile devices, and sometimes made it hard and frustrating to figure out what to do next.  After going back and forth many times, I settled on a bar at the top showing any interactive words that were scrolled off the top of the screen.  Although this detracted somewhat from the UI and the gameplay mechanics of "hunting" for the right word, most players seemed to prefer it.


## Conclusion

I think my hypertext experiment worked, and I am pleased to release "Darkness" as a new medium-length interactive fiction piece.  I'm very excited about the changes in my new engine.  I think that not only can Twine-style games add a new dimension to games built on my engine, but my engine can add a new dimension to Twine-style games.

Ultimately, I'm excited about the customization options available, and I look forward to seeing other creative applications.  I believe that with the new engine, game developers and story tellers can make almost any kind of interactive stories they can dream up.
