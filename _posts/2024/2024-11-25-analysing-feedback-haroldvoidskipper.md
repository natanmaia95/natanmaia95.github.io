---
layout: post
title: Analysing Feedback on Harold Voidskipper
date: 2024-11-25
#description: an example of a blog post with table of contents
tags: personal devlog
related_posts: false
toc:
  beginning: true
---

I just came back from showcasing Harold Voidskipper in a convention called _Feira do Conhecimento_ (Knowledge Fair) alongside other dev friends.
For a jam game it has given me a lot to think about in terms of level, combat and UX design in how many different people got to play it. There was the
original jam, two entire conventions with many school students as attendees, and a handful of gamedev gatherings, and all of those gave me a bunch of
stuff to think about.

At one point I had so much to parse that on day 2 of this last convention I felt it was fine to leave the game unattended for a bit (there were other people guarding my stuff at least) 
while I used more of my time to socialize and network with the other devs. I needed time to process all the feedback, and writing this blog post is part of that.

In this post, I'm writing in a very unfocused manner on what I got from all these test sessions, and what info I can use moving forward for my immediate next projects. 
I'm also treating this as a Post-mortem of sorts for Harold Voidskipper as I move full steam ahead into my next projects.

## Context

_Harold Voidskipper_ is a game I made during Harold Jam 2024, an event celebrating RPGMaker games with their tropes and little default characters,
but didn't require the games to be made in that engine (so I told a little story with the default characters in Godot instead). 
It's an action game with a cutesy aesthetic, and a control scheme inspired by Enter the Gungeon with twin-stick shooting and dodge rolls, with a
bullet hell final boss to match that intensity in mechanics. It's one of the first projects where I focused on polishing and visuals as combat was already implemented in another project and just moved over.

_Voidskipper_ (no Harold here) is what I'm calling my next game project that inherits its combat engine from Harold Voidskipper, but not necessarily
design. Throughout this blog post I'll be approaching Voidskipper as a game which sells itself as a "Character Action Game for babies", a nice 
Unique Selling Point or USP inspired by the in-depth movesets the copy abilities in recent Kirby games have. The concept is built on top of a Nintendo-style
difficulty design of having very accessible main progression with progressively difficult extra challenges culminating in tough tests of skill.

Right, let's get into the notes!

## General Combat

Only 5% of players understood how Potions worked without any intervention. Between the UI being subtle, the red XBOX B icon next to it not looking like a button and not matching my test controller 
(switch pro controller), and me forgetting to show the button icon alongside the keyboard SHIFT icon in the npc tutorial (70% of players missed the entire dialogue btw, not even touching that npc), 
it wasn't clear how to trigger it. Yes, TUNIC does it similarly, but still. When they did trigger it (mashing, etc), they missed its meaning because to prevent accidentally using your potions 
and for combat design I made you have to hold B for half a second, but the animation was recycled from the spark ball attack (it's a game jam game) 
and didn't make it clear something different was happening AND you had to hold the button for longer.

For the conveyance problem with potions, there are a few solutions. I could make the time to heal faster up to .2 or .3 seconds. I could make a discrete
animation showing Harold drink the potion gradually like you see in Dark Souls or Monster Hunter, or I could've showed a bar above his head that fills
as you hold the button, similarly to how Kirby shows the "Drop Ability" command bound to Nintendo A, or how modern games have actions that ask you to hold a
button (open chest, skip cutscene) and those have a progress circle around the object or button prompt.

Many players didn't even know they had potions! They likely mashed through or skipped the tutorial npc mentioning "using your potions", and didn't parse the HUD graphic as a potion with X uses remaining. 
A good way a friend mentioned for remedying this was to have the player _obtain the potion themselves_ as a drop after an enemy encounter or something, 
as if they have collected something, they'll know it exists and will want to know how to use it. 
For the future, however, I might ditch that altogether and just do tiny health collectables like most action games have enemies drop, and before bosses award the player 
with a massive chest of healing orbs like God of War or Darksiders do. It's automatic and requires less tracking of info from a player.

In the next section I mention how many players missed either of the two attack actions, Sword Slash and Spark Ball. 
One side effect of this is that I got to see people playing with a limited moveset, _unintentionally_. 
This showed me that, while the sparks are balanced to have lower damage output to not undermine the sword and its low range, playing using only sparks is not satisfying and really boring.

## Friendliness and Accessibility

_Voidskipper_ has a more general target audience, as per the Nintendo-like direction, and thus I want to appeal to people
with a bit less experience in games, but still let them have a good time and feel powerful. In that sense, having two conventions
where I got middle and high school students to play the jam game was an amazing opportunity.

I got to see first-hand that twin-stick is not obvious to new players, especially on controller (the main control scheme for 95% of tests).
People don't have the tendency to use the right stick, usually the camera stick, in 2D games, and younger kids don't feel comfortable with using the
right stick when they need the thumb to mash the face buttons. The jam game also didn't require the player to aim at any moment as when not touching
the aim stick the attack direction is the player's moving direction instead, so players weren't forced to try out the stick like they would be in Gungeon.

Even then, despite experienced players telling me my twin-stick feels super smooth and responsive (if not a bit too snappy and maybe capable of giving someone motion sickness), 
many players tried the twin-stick and gave up on using it as it required attacking with the triggers, and they wanted to attack with face buttons instead, and as such their thumbs were busy.

Similarly, younger players also don't use the shoulder and trigger buttons at all, as it literally halves their grip on the controller, which may either be
big, heavy, of an unfamiliar shape, or any combination of those. I had the foresight to patch in alternative face button bindings for the dodge roll and both attack actions before the cons, 
which did help, but many people missed the Magic Attack bound to XBOX Y because the attack button is usually XBOX X, and if they pressed Y too close to an enemy the spark ball would spawn and immediately disappear, 
with a sound effect but no visual particle for the hit, which was less satisfying. Many players assumed you could only use the sword. 
Some also assumed you could only use the sparks, after all "I found the attack button, what else would I need?".

On the topic of face bindings, many Mario and Kirby games bind the same action in multiple buttons, and I have two guesses as to why:
- Provide the new player an easier time grasping the basic verbs by mashing buttons instead of tutorials
- Provide the experienced player a choice of whatever position is most comfortable (doubles as an accessibility factor for people who can't press a specific button!)
Taken to the extreme, you get the Masahiro Sakurai school of 1-button design, used in Kirby Air Ride and other projects of his. In Kirby Air Ride, you have
one action button (the big green A on your gamecube controller) that takes care of braking and drifting, boosting and grinding, attacking and stealing items.
If players still somehow miss that (including the short tutorial), the L and R buttons are also bound to all of those actions, for redundancy. I am open to corrections, though, as there's probably a third reason for this I haven't figured out.

I think the cutesy artstyle with chibi characters and stars and vibrant colors also helped attract a more general audience. Averaging the entire duration of
this last event I saw a very rough 50/50 gender split on who came to my little TV stand, as well as who stayed for more than 2 minutes (dying once or twice).
Compared to some of my friends with more gritty games who saw mostly high school boys check them out.

I do have to mention, the players who endured the game for more than two levels (eventually leaving when the difficulty got cheap i.e. swamp and cave maps)
were 4 older boys, 1 girl, 2 adults, and other devs.

## Conclusion

The main conclusion here is that I'm bad at writing post-mortems XD

Voidskipper is shelved so far as I level up stuff like enemy pathfinding and AI, so when I'm eventually
free from university work I can probably pick it back up. I'm looking forward to it though.