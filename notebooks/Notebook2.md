# Design notebook entry

## Last week's critique

My reviewer for last week's work affirmed the dialogue I had with my previous reviewer about designing my code base with future expandability: it would be nice to do, but beyond making my code flexible enough to make week-on-week project work simple, my efforts should be focused elsewhere. It was helpful to have another opinion on this topic. My reviewer also gave me some really useful ideas on how to handle locked doors within my game. To motivate this, I was questioning whether to implement locked doors as an item within the game or as a property of the relevant Room class. They suggested that out of those two options I go for implementing it as a property of a Room, but they also suggested creating a new Door class that can exist as a node in between each connection in my network of rooms. If the door is open then it allows the transition, but if it is closed it will wait for an interaction with the right item before it can become open. Both of these are viable solutions in my opinion, and in the next week I'll be deciding which one to code up! 

## Description


I started this week by thinking a lot more about my DSL syntax as it pertains to characters and items within the game world. In this process, I made a lot of additions and changes. The first notable change is that I've removed the top-level rooms tag, and each room will sit at the top-level, with the items and characters within each room nested within. I made this change because I want to support multiple files combining into one game, and this makes it easier to write rooms in whatever file you want and have them merge together at compile time. To discern between characters and items, I've settled on the first option being 'item' or 'character' to tell these things apart. In addition, items can open doors or other items, can be grabbable (meaning it can go into your inventory or not), and can have a series of texts that print out upon looking, using, or picking them up. As for characters, you can specify any number of thing/text pairs - to be asked by the player in an 'ask character about thing' structure - by specifying the thing and the text separated by a colon. Finally, I've added start and end options for rooms to specify start and win states for the game. I also wrote in additional text for rooms conditional on some event occurring (like a key being used to open a door), but I'm not sure whether that will actually get implemented...

Here's that expanded syntax below. There are still things to be sorted out that have been hinted in the comments at the top:

```
# Needs to support multiple items interacting on another item/door
# Not quite satisfied with the blocked syntax... too imprecise
# Should maybe revise 'opens' syntax to something more general like 'interacts with', but that's longer and can be a confusing descriptor in the case of locked doors


<dark>(dark is start, treasure is north, cave is south, win is west) {
    default: You find yourself in a dark room. A door leads to the north, while a cave opens to the south. A mysterious locked door also lies to the west.

    <key>(item, grabbable, opens chest) {
        look: blah
        pickup: blah
        use: blah
        }
    
    <apple>(item, grabbable) {
        look: blah
        pickup: blah
        use: blah
    }

    <beggar>(character, gives apple) {
        apple: Some text
        bucket: Some more text
        door: Even more text
    }
}

<cave>(dark is north) {
    default: You've arrived in a dingy cave. You can go north to return to the starting room.
}

<treasure> {
    default: Wow, there's a treasure chest in here! You can't open it though (at least not yet). The starting room resides to the south.
    after key: You've opened the treasure chest already! The starting room resides to the south.

    <chest>(item, contains door_key) {
        look: blah
    }
    <door_key>(item, opens west of dark) {
        look: 
        pickup:
        use:
    }
}

<win>(blocked until door_key, win is end) {
    end: Congratulations! You have escaped the dungeon and won the game.
}
```

My original plan was to implement items this week, but after doing this syntax work I realized that items would be a very significant (and time-consuming) part of the project. So I decided to work up to items and implement characters first. To do this, I first pared down my adventure-expanded file to include only rooms and characters. You can see that syntax below:

```
<dark>(treasure is north, cave is south, win is west) {
    You find yourself in a dark room. A door leads to the north, while a cave opens to the south. A mysterious locked door also lies to the west. There's a beggar in the corner with a bucket of apples (maybe ask them about it?)
    <beggar>(character) {
        apple: Yes, those are my apples.
        apples: Yes, those are my apples.
        bucket: Do you like my bucket?
        door: Go through that door if you dare
    }
}

<cave>(dark is north) {
    You've arrived in a dingy cave. You can go north to return to the starting room.
}

<treasure>() {
    Wow, there's a treasure chest in here! You can't open it though (at least not yet). The starting room resides to the south.
}

<win>() {
    Congratulations! You have escaped the dungeon and won the game.
}
```

I then had to modify my parsing code to accept characters in the form written above. Once that was done, I had to build a lot of dictionaries on the backend. Each character needs a dialogue dictionary that stores things as key and corresponding text responses as value, while each room needs a dictionary that maps character names (ex. beggar or knight) to corresponding Character objects. It took a while, but that functionality is now complete. In a game, you can now use 'ask character about thing' syntax and it will print out the encoded responses if the character and thing both hit in the relevant dictionaries. If not, placeholder "I don't know who you're talking to"/"I don't know what you're talking about" text is printed instead.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issues with my project are making decisions on the last few DSL things with items and then implementing it all in my artifact. This will be the bulk of the remaining work (aside from user testing and potential syntax revisions in the last week), so I'm expecting this to take the better part of two weeks to accomplish.

**What questions do you have for your critique partners? How can they best help
you?**

* Any feedback on my expanded DSL syntax and advice for the open questions on items would be very helpful! In particular, is the current verbose style of my syntax good for my audience (first-time programmers), and would a secondary, more succinct syntax be worth implementing?
* Like last week, any comments on my parsing strategy would be nice. As I move into items, I probably will need to expand into pyparsing's parse actions functionality, so any words on that would be really appreciated.


**How much time did you spend on the project this week? If you're working in a
team, how did you share the work?**

About 5-6 hours.

**Compared to what you wrote in your contract about what you want to get out of this
project, how did this week go?**

The original plan was to implement items this week, but as specified earlier I changed course and implemented characters instead. As I'd hoped, I think implementing the characters first has given me a good foothold for implementing items (on both parsing and backend data management).