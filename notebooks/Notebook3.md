# Design notebook entry

## Last week's critique



One piece of feedback I got last week was some notes on my DSL design, the most important of which being that having to list 'item' or 'character' when you're writing one of those things is tedious. I'll have to explore other ways where I can make this distinction clear to my interpreter without listing that out. Maybe I can replace those words with a shorter symbol, or maybe I can code things such that it can intuit whether it's an item or character based on what options are provided within the parentheses and brackets.

Another significant piece of feedback I got last week was to be mindful of my error handling when it comes to parsing my external DSL. For my project, this error handling comes in two forms: errors from the initial parse (from pyparsing) and errors resulting from my own data management (getting it into a form my backend will accept and checking for any errors in the stated logic - bad room connections, locked doors requiring keys that don't exist, and so on). Pyparsing does return error messages, but they aren't particularly user-friendly - just stating that it saw X character when it was expecting Y character - and I'll be looking into ways to override the default error messages in place of my own. For example, invalid matches on an item should return that instead of the expected character thing it currently does. It was really helpful to get some thoughts on this last week. While I didn't get to work on it this week, error handling on both of these front will be a major focus of my final week and a half of project work. 

## Description

This week was a total focus on adding items to my DSL and to my backend, then writing the parsing/interpreting to make it all work together. I knew going in that this would take more than one week to accomplish, so I focused on a subset of things that I felt were most important:

* Adding grabbable items to the player's inventory
* Using items on other items (leading to consequences and the item leaving your inventory)
* Supporting items that contain other items, like a chest

leaving features like locked doors and characters giving items on certain lines of dialogue for next week. I also felt that getting the listed things working would make what remained a lot easier.

I started by producing some DSL lines that would include all these new features. It includes a key in one room that unlocks a chest containing gold in another room:

```
<dark>(treasure is north, cave is south) {
    You find yourself in a dark room. A door leads to the north, while a cave opens to the south. A mysterious locked door also lies to the west.

    <beggar>(character) {
        apple: Yes, those are my apples.
        apples: Yes, those are my apples.
        bucket: Do you like my bucket?
        door: Go through that door if you dare
    }

    <key>(item, grabbable, opens chest) {
        look: It's definitely a key.
        pickup: You've grabbed a key and slipped it into your pocket.
        use: With a snap, the key slides into place and unlocks the chest.
    }
}

<cave>(dark is north) {
    You've arrived in a dingy cave. You can go north to return to the starting room.
}

<treasure>() {
    Wow, there's a treasure chest in here! You can't open it though (at least not yet). The starting room resides to the south.

    <chest>(item, contains gold) {
        look: It's a chest.
    }
    <gold>(item, grabbable) {
        look: It's very shiny!
        pickup: Congratulations, you have found the magic treasure that makes you win the game!
    }
}
```

From there, I wrote all the parsing code (using both the pyparsing package and my own code from scratch) such that all the info laid out in the DSL is imported into the backend and the game can run. As of right now, all the items are properly assigned to each room, and you're able to 'look at' them and it will print out the proper text. I still need to work on the backend to support the inventory system and item interactions. So not as much has been done as I hoped this week, but I have a few work hours on Monday before studio time, and I'll update this notebook if anything meaningful gets accomplished then!

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue is finishing up the backend of my current items workload and implementing what was left out my items list for this week. Once the implementation is done, there is still a good amount of error-handling and testing to be done to make sure that my code is robust and intuitive to use.

**What questions do you have for your critique partners? How can they best help
you?**

* As always, any notes on the external DSL syntax I've presented here would be helpful.
* For error-handling, is there anything I missed in my 'Last week's critique' section that will be important to implement?
* There were a handful of stretch goals that I outlined in my project pitch. I'll list them again below. I'm looking to implement one or two of these in my final product, and I'd love to hear which sound the most interesting or important!
    * Support for ASCII images on certain triggers (such as entering a space or picking up an object) - would be loaded in similarly to how images are handled in Markdown with parentheses around the file name.
    * Adding support for more complex player commands like combining objects and having extended conversations with non-playable characters (asking them about places and objects).
    * Exceptional examples in my provided documentation - a good example of this would be implementing a chunk of an actual text-based adventure game from back in the day, I'm partial to [*The Hitchhiker's Guide to the Galaxy*](https://en.wikipedia.org/wiki/The_Hitchhiker%27s_Guide_to_the_Galaxy_(video_game)).
    * Exceptional error-catching and debugging approaches - I think that a custom debug mode that can print out all the objects in each room and their relevant interactions would be really cool

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I spent about 5 hours this week working on my project!

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

While there's plently left to do, I don't think I'm in a terrible place. My goal for this next week is to finish up the items implementation, solicit feedback on my DSL design (from classmates and from Prof. Ben), and make improvements on that front as needed. For the last four or five days after that, I'll be creating some example game files, recording my demo video, writing documentation, and implementing one or more stretch goals. Right now I'm leaning towards the ASCII images one, but if this week's reviewers think other options on the list would be better I'll definitely consider their feedback!