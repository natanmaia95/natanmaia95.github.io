---
layout: page
title: Amazon Crash
description: prototype for 2D action boss-rush
img: assets/img/projects/amazoncrash_thumb.jpg
importance: 1
category: prototypes
---


<div class="col-sm mb-3 mt-md-0 text-center embed-responsive embed-responsive-16by9">
    {% include video.html path="https://www.youtube.com/embed/indFQUKboBA" class="img-fluid rounded  z-depth-1" %}
</div>

This is a prototype for a 2D action game made in a couple of weeks. Me and a friend wanted to make it a sort of boss-rush game with different enemies as an opportunity to learn about godot, but we sadly moved onto other projects after a while. 

When thinking about what an action game needs first and foremost, I think movement and actionsets. For enemies, I control their attacks and behaviors using a single State Machine, mostly taken from <a href="https://www.youtube.com/watch?v=DPxIMVC0oZA">this video</a>. Transitions from state to state could be triggered by conditions specific to each enemy, like their health total, or their line of sight to the player, or internal timers. 

<div class="text-center">
    {% include figure.html path="assets/img/projects/amazoncrash1.png" title="" class="post-img-fluid rounded z-depth-1" %}
</div>
<div class="caption">Your average state machine, with child states.</div>

Each player attack is also handled with those same state machines, not unlike character action games. I thought making transitions between states could lead to some sort of "combo strings" using just two attack buttons. So, each attack state is tied to an animation that also sets which frames you can roll-cancel and which frames you can input to start another attack, and if an input is triggered when the roll-cancel boolean is active, the player transitions to the Roll state and so on.

<div class="text-center">
    {% include figure.html path="assets/img/projects/amazoncrash2.png" title="" class="post-img-fluid rounded z-depth-1" %}
</div>

<div class="caption">Animations handle moving hitboxes and i-frames.</div>

In the end, it has a decent and modular system for action games with combo strings, like you see in the Monster Hunter games with their complex weapon movesets. I had three different weapons in the demo, a sword, a spear and a bow. Sword and Spear attacks could weave into each other, while the bow had an entirely separate flow. There's room to use multiple state machines for various parts of a character's moveset, and combined with some system to buffer inputs it could be very powerful. 

<div class="text-center">
    {% include figure.html path="assets/img/projects/amazoncrash3.jpg" title="" class="post-img-fluid rounded z-depth-1" %}
</div>

<div class="caption">Average weapon flowchart from Monster Hunter</div>

The <a href="https://github.com/NatePlays95/Amazon-Crash">Github repo</a> is public if you want to check it out. I would love to find an excuse to use this in an actual project soon.