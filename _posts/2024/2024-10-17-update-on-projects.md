---
layout: post
title: Update on my Projects
date: 2024-10-17
#description: an example of a blog post with table of contents
tags: personal devlog
related_posts: false
toc:
  beginning: true
---

I forgot to update the blog in september due to a very confusing uni finals season, but that's over and I've got my well deserved break.
So here's what I have been working on in the meantime!

# Movement FPS

It's a very rough prototype of a movement shooter like Titanfall or Severed Steel, although more grounded.
LoboGuarah is working on it with me, and our vision is not fully thought out yet but the idea is to reward the player
for doing cool movement techniques with points and speed.
I made a <a href="{{ site.url }}{{ site.baseurl }}/projects/movement_fps/">project page</a> for it, 
although it has less details than the rest for now.

Guarah is the main designer and he's saving some time to actually work on level design, but until that comes I don't
have a lot to do on the project.

# Cute Pomodoro

There's also this desktop app I've made in two weeks. Cute Pomodoro is very simple, just some text notes you can add
and a clock you can use to measure your tasks. It also has a <a href="{{ site.url }}{{ site.baseurl }}/projects/cute_pomodoro/">project page</a>.
Made it because my boyfriend suggested it would be a nice idea to replace his physical post-it task board with a digital one.

I still need to make a release build to upload to the Github. All that's left is to fix some bugs.

# Minecraft Mods

Part of my break time (and finals procrastination) was dedicated to learning Minecraft Modding again, when I saw a new tutorial
series for NeoForge. I already had some assets from an older project so after doing a few tutorials I started porting them.

I'm making the Palicos from Monster Hunter as minecraft pets, with some design oriented to "lifestyle" features like animations,
clothes and skin patterns, learning skills on level up and such, a similar direction that Cobblemon and Digimod take.
Here's a showcase of armor sets I've made, including halloween-themed ones for this month.

<div class="text-center">
    {% include figure.html path="assets/img/posts/2024/palico_armors.jpg" title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">Making these has been a lot of fun!</div>

I also implemented some of the weapons from the games, as well as a leveled skill system on top of vanilla enchantments,
which armor and weapons can have. They're not balanced (nor tested at all). I'll first get the damage formula, including
a custom defense stat and elemental stats, ready and usable, to then start making armor sets.

There are no intentions of making this a full mod with continuous development (aside maybe releasing the palicos standalone),
as it's more of a "programming toy" for myself. There's already a monhun mod on the way called Monster Hunter Endless Frontier
which focuses on pretty monsters and animations ~~and a cuter palico model than my own~~, as well as being a full conversion
with quests and pet slots and weapon slots. I just want to play with monhun elements in Minecraft, which is a different direction for sure. 

I'm also making a food-themed mod with friends for an event called <a href="https://modfest.net/1.21">ModFest</a>, but we don't have lots to showcase just yet.

# Silver Daze

Sawyer's work on Silver Daze has slowed down a bit, which left me not a lot to help with. He's working on one of the final zones 
that starts wrapping a few story beats and had some more complicated gimmicks to figure out. However, that zone does bring a new...
without giving away anything... "quest style" with some fancy HUD elements I can't wait to work on. 
Looking forward to showing that off when it's close to done.

We also made a <a href="https://bsky.app/profile/gemgames.bsky.social">Bluesky account for Gem Games and Silver Daze updates</a>
which I'm mostly in charge of managing, but I've been at a loss of what to post sometimes.
I also need a better recording setup than "Windows Screen Capture", this might be a reason to learn DaVinci Resolve again. 

I'm also aware Bluesky is a lot more social and a lot less marketing-focused than Twitter, and as such an account exclusively for game news
and screenshots wouldn't get a lot of traction, but I want to have _some_ visibility for the game, and nobody on the team understands
vertical content like tiktoks, yt shorts or instagram reels.

# Voidskipper

Some updates to <a href="https://nate-the-bard.itch.io/haroldjam-2024">Harold Voidskipper</a> are due, 
but I've been working on Movement FPS while I figured that out. 
I plan on adding a pause screen, an options screen and some way to lock the cursor on the window. Everything has been
implemented _in the FPS project_ and just needs to be ported over.

That being said, I did mention before that I wanted to make it into a larger game, with more bosses and more replayability.
I accidentally ballooned the scope in the GDD and it would be a 6mo - 2y project, which scares me. 
I can't see the game having more content (and removing the RPGMaker theme) without _rebuilding it_ and making an effort to make
a game that's not over after two hours. 

And I just think I have better things to do with that time, like honing my skills for a work portifolio (frontend? backend? I'm not sure yet)
or experimenting with more jam games. I will still pick up the project, especially as it's going to be my playground for 
"2D combat" features I want to try and implement, but aside of a decent GDD I'll share another day and a cloudy vision of what I want the
game to be, _it's currently on pause_.

# What's next?

I want to set aside some time to study Shaders and Game VFX in general, as well as in regards to creating those in Godot.

I also want to learn about making websites but while I understand the technologies (I have made react and react native front-ends before),
it still doesn't hit me how to actually set up, test, host and share websites. Most tutorials I find just teach you how to do HTML-CSS which I already know.

Will get to work on improving Harold Voidskipper so I can turn that leaf and start playing with advanced combat mechanics.
And I'll wait for Guarah to get back to work on the Movement FPS, we have lots of ideas to try still.

Also, if you don't already know, I have a Bluesky account as well, <a href="https://bsky.app/profile/natanmaia95.bsky.social">natanmaia95.bsky.social</a>!
I sprinkle updates on my projects here and there.