# Design notebook entry

## Last week's critique

In last week's critique, Lilly advised me to prioritize my work on error-handling for things that will most commonly go wrong. I think this makes a lot of sense, and based on this feedback I've decided to focus in on DSL syntax errors (because they'll be super common) and logic errors within declared code (as these would be super annoying to debug). I plan on doing the former using setFailAction calls in pyparsing, while I'll handle the latter with custom exceptions in my own processing code.

I also got feedback on my stretch goals: that adding ASCII images would be the best one to go for. This was my impulse too, and I'm glad that I got a second opinion on it. It should be fun getting to work on this between now and Friday! And once I solidify the relevant DSL decisions as well as how the file system should work, it shouldn't be too hard to implement.



## Description

This week I started by implementing the rest of my basic item feature set on the backend. In terms of commands, now you are able to pick up items and use them on other objects. Some subtleties to this include being able to put items within other items (like gold within a chest) and have these items be automatically picked up when the container is opened. Finally, the 'inventory' command now works, where it will print out the names of all the items within your inventory. With this, all of my intended user commands are implemented! 

Aside from these item features, I added a capability to my DSL where you can write 'start' in a room to signify that the game should begin in that room. I still need to add an 'end' tag into my DSL, where the intention is that you can add it to a room or an item and when you enter that room or pick up that item the game will end. 

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing thing is to finish my implementation once and for all so I can solely focus on finalizing my DSL, doing thorough error-handling, and writing up proper documentation. 

**What questions do you have for your critique partners? How can they best help
you?**

* I'll throw my list of supported commands within the game below: My question is would you change anything about how these work or are phrased?
    *  go X : where X is a cardinal direction
    * ask X about Y : where X is a character, Y is an character or object
    * take X : where X is an object
    * use X on Y : where X is an object in your inventory and Y is another object
    * look at X : where X is a character or object
    * inventory : returns contents of player inventory
    * exit/quit : quit the game
*  When I add support for ASCII images to my DSL, how should I handle file names and locations? Should they have to be in a specific folder relative to the .game file or should it be more flexible? Should you have to give the file extension or not? Should both absolute and relative filepaths be supported, or should one be prioritized?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

I spent about 5 hours this week working on my project.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

The plan for this last week (that I set in the previous week's notebook) was to get all the implementation done and revise my DSL as appropriate. The senioritis definitely hit me this last week, as I fell short of these goals. From now until Friday, I'm just gonna need to prioritize getting my project across the line. While not ideal, that's alright, as this project is my only major deadline this week!