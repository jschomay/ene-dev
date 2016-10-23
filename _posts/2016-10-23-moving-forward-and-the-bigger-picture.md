---
layout: post
---

When I started making this framework, I had planned for it to be completely code-driven.  I took inspiration from other code-based storytelling tools, such as [Inform 7](http://inform7.com/) and [Ren'Py](https://www.renpy.org/).  I put a lot of attention into making a very clean and simple API for story authors.

I also originally designed the framework to be very opinionated about what types of stories it would tell, and how they would look, without giving much control to the story authors other than defining their story world and how it progressed.

In my ElmConf presentation, I casually mentioned how using Elm and a data-driven could allow for neat things, like making a visual story editor.  It was an interesting point, but not one that I took too seriously.

Then five things happened:

5. My friend kept challenging me to "open up" the framework as a general purpose story-telling tool, allowing for more customization.
1. After my presentation I received a couple intriguing comments along the lines of, "There's something bigger here that you have tapped into that you don't see yet."  What could they mean?
2. I met Greg Ziegen, who is building a [RPG game engine](https://youtu.be/rLSrQjYFVoU?list=PL8wLtAjUdVWCX45d2dWbM3KDADYJgImet).  His requirements and approach overlaps with mine, and we spoke about the challenges and implications of making a truly data-driven framework.
3. I was contacted by a person who made their own story with my framework, who wanted a way to embed the story engine inside his existing Elm app, which was an interesting request.  I also found it very enlightening to see a story built by someone else, and in in particular, the unanticipated, but delightful customizations he made.
4. I had the awesome opportunity to do an [api design pairing session with Evan Czaplicki](https://youtu.be/De1c85B4Zxs), creator of Elm.  Besides improving the code, talking with Evan stirred up many new, exciting possibilities for a more involved and fully-featured Elm Narrative Engine.

All of these points of inspiration bounced around in my head, and eventually it became pretty clear to me where I wanted to take this.

<!--more-->

## The big picture

My driving vision has always been "How can I make it a simple as possible to make stories that are as engaging as possible?"  I wanted this tool myself for my own story projects, but I also enjoy seeing what other people make.  And to get a larger community of story authors, I need to make the tool very accessible.  My vision will remain the same, but the scope will be much larger.

The plan is to make a whole platform that uses the Elm Narrative Engine at its core.  The platform will have the following features.

### A visual editor for telling interactive stories

The visual editor is really the "killer app" for the engine.  It will make it very easy for anyone to create engaging and dynamic interactive stories in a sleek web interface, with a live story preview, no coding skills required.


### Story debugging tools

The hardest part about making an interactive story, is getting the rules correct.  You need to be restrictive enough that your rules don't trigger before you intend, and you need to be sure that all of your rules are reachable.  The only way to test this is through manual play-testing.

Speaking with Evan brought up some interesting possibilities for story debugging tools to automate this process and give warnings if there is a problem with your story.  In Evan's tongue-in-cheek comment, "Your story may not be *good*, but at least it will be *correct*."


### Story hosting and discovery

Once you finish your story, what do you do with it?  Part of the platform will act as a portal where you can submit your stories as well as find other people's stories to play and discuss.


### Story exporting and advanced customization

For more advanced developers, I will still offer the engine as an elm package, but with expanded API's.  The current version of the framework is extremely controlling, offering little opportunity for customization.  That will all change, with an option to export your entire story "config" as JSON data to use in your own code base.  This means developers can use the visual editing and debugging tools of the platform to write their story, and then do just about anything they can think of in their code to extend it into something completely new.


## Technical implications

I am excited about the possibilities all of this will open up.  However, it does create some very challenging technical considerations.

The main requirement for everything to work is to be able to represent the entire story as data -- not just data, but *serializable* data.  This is because it will be necessary represent story data in JSON for each component of the platform.

Serializable data means two things -- no functions in the model and no dynamic types either (because I have no way of dynamically turning a string into a type).

The latter is a concern because it means losing all of the type safety that the engine currently provides, such as ensuring characters don't get mixed up in the inventory, or a rule that is expecting a location won't be given an item.  This means that I'll need a new representation of the model, and I will need to rely more on the GUI and validations to ensure a valid model.  In essence, by definition, I am forced to move validation from the compile-time type checking to the run-time, but that is what allows for the new features, so it will be worth it.


## Up next

I am currently working on version 2.0.0, which finishes some of the plans I didn't get to in version 1.0.0, but also involves a lot of refactoring to explore and pave the way to the new ways of representing data that will be needed moving forward.

I welcome any feedback you have on the direction I am going, or features you would like to see.

And so, the story continues...
