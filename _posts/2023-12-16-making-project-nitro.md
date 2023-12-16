---
layout: post
title: Making Project Nitro
date: 2023-12-16
#description: an example of a blog post with table of contents
tags: devlog project-nitro
related_posts: false
---

Last week I made <a href="https://nate-the-bard.itch.io/project-nitro">Project Nitro</a> public in my itch.io page, so I'd like to write more about the process of taking it from idea to prototype. This one is a long read as there's so much to catch up with, but I'll try to write shorter posts next time 😅.

## Idea

I love cars and racing, and I love making games, so of course the idea of making my dream racing game has been with me since I learned Construct 2 back in 2018 and made my first little games. Back then, there were attempts at making silly browser racing games from me, but between not knowing many programming patterns and not being satisfied with my driving physics, I scrapped all of them.

Fast forward some 5 years, uni assignments are slowing down and I'm getting bored. I've already made better driving models since then, but not a lot more than following tutorials from internet people and doing some research on the side. I was on the low of dropping from two game jams and almost dropping a third, so I decided to get on with a pet project. Well, if I already have the driving systems online, how hard would it be to make a little game around it?

<div class="text-center">
    {% include figure.html path="assets/img/devlogs/making-project-nitro-0.png"  title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">This wasn't my first rodeo, at least with cars.</div>

## The Plan

First, I'd adapt the driving model to be a bit more arcade-y. I was playing some Mario Kart and Ridge Racer at the time, so I, ahem, "borrowed" some assets to help match the feel. Then, I'd need to make a few tracks, and some way to make progress in them and complete laps. Finally, I "just" needed to get AI and items in, and make something like Blur where you choose a car, an event, you race with powerups on the track, and get points on victory.

I definitely overscoped it.

I just wanted to know if I knew how to make a game out of my car system, I didn't need it to be "market-ready" or anything. What if I spent 12 months on the project and it wasn't fun to play, or the codebase was a nightmare to work with? Something smaller was enough for my purposes.

So the plan eventually ended on: Make a few cars, a few tracks, a Time Attack mode, and menus to go back and forth. That would be my prototype, and if it had good reception and I _actually enjoyed making it_, I could expand it to an actual game in the near future.

#### controls and camera

My original simulation model was twitchy and required very precise inputs. I knew I wanted the game to be more arcadey and accessible in general, so following <a href="https://youtu.be/n_A0RqeGado?si=eni13AUtXr2w-OrA">this GDC talk by a veteran at Criterion Games</a> and playing a bunch of NFS Hot Pursuit Remastered, I went with the following approach:
 - Make more accurate simulation systems first;
 - Add constraints and assists as needed.

The suspension is your usual Raycast Suspension, and both engine and steering use simple applied forces to the rigidbody. To drift, I decrease the car's traction to the ground and add an extra lateral force for good measure, it's unrealistic but it's fun like old racers. There are also "assists" to apply brakes if the car is rolling down a slope and the throttle is off, and assists to roll the car straight if it is airborne.

#### on tracking race progress

The modern method nowadays is to use a spline or path throughout a track, and have cars match to the closest point in that spline. Godot Path3D nodes are still kinda funky so I went with a simpler approach: good old Checkpoints.

<div class="text-center">
    {% include figure.html path="assets/img/devlogs/making-project-nitro-checkpoints.webp"  title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">Checkpoints in Mario Kart are a tiny bit more complicated than this.</div>

Implementations can vary, but the idea is simple: To complete a race, you must _hit_ all checkpoints, possibly in order. Sometimes some checkpoints can be skipped, so games use "key checkpoints" for race validation, and the smaller checkpoints for race progress. To rank drivers, check their last checkpoint, and in case of a tie, check the distance to the next checkpoint.

I only mention this as it came back to bite me later: making AI drivers follow checkpoints was much harder than following paths. I'd need a "racing line" Path3D for computer drivers either way. This choice single-handedly made me not want to add AI drivers in this prototype, so I'll be leaving those for a future project.

## First Playtest

In my city we have a little event organized by some friends of mine, where small game developers bring their projects for other to play, give feedback, and network in general. It's more of a "community gathering" sorta thing, although we do receive local indie studios there as well, and it's monthly, so having started the project in October, I should be able to take it to two gatherings before the end of the year.

I didn't get to go to the first gathering myself, but a friend brought the demo and took some photos.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-1.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-2.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-3.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">Photos from the first playtest event. You can see the placeholder assets.</div>

Some bugs aside, it seems people enjoyed the build. By then I had added the Time Attack feature, and according to my friend some of the visitors there were even competing for times. I couldn't have heard anything better from it.

As for the bugs, the game had poor performance on the cheaper machines in the venue. Sure, I was using shadows and many light sources in that build, but "it ran at 200 FPS in my gamer laptop, so there shouldn't be any problems". For that reason, I switched the project's rendering pipeline in Godot from the Vulcan based Forward+ to the at the time very incomplete OpenGL Compatibility pipeline. It didn't even have support for shadows back then, so I was forced to make it light on resources haha.

#### swapping assets

Now I just need to swap the cars and tracks. I mean, a track is a track, any layout should do right? In my first attempt, I just copied some curves from the Bernese Alps track in Forza Motorsport 4, a simulation racer. It took me some time tweaking materials and road camber to match. It felt great to drive in the original game from all the different corners and elevation changes, so I felt confident it would fit.

<div class="text-center">
    {% include figure.html path="assets/img/devlogs/making-project-nitro-4.jpg"  title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">Realistic? Sure. Fun? Not very.</div>

I couldn't quite pinpoint why it felt bad to drive on the track, yet the stolen tracks from Mario Kart were really nice and fun. And no, it wasn't the visuals, the car was quite fun on top of a white test cube. That was, until I finally gave up and made a test map with cylinders of various sizes to test cornering:

<div class="text-center">
    {% include video.html path="assets/video/devlogs/making-project-nitro-cylinders.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false %}
</div>

The corners in the Alps replica were either too wide and shallow to drift (and unlike a sim, the simple act of cornering wasn't a challenge), or were too acute and low-speed to do high-speed drifts, which I think is the most fun part of a Mario Kart-like driving model. The placeholder tracks had wide enough corners to carry long drifts in, and sharp enough corners to test reaction time and racing lines. That day I learned track design is actually harder than it looks.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-corner1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-corner2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-corner3.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">Corner sizes were determined from the driving model. Yes, the car is not accurate to real life scale.</div>

I used the built-in CSG nodes in Godot to prototype the levels, which ended up being very painful as my driving model would bug out here and there, the pieces are had to lay out on the scene and somehow even harder to pick with your mouse cursor if they're in clumps, and I again forgot you could use Path3D nodes to lay out CSG meshes to shape a track. I need to learn a new workflow (probably a blender-first, engine-later flow) if I want to make more of these maps.

Finally, the Ridge Racer car models needed to get out. The date for the second playtest event was approaching so I didn't want to model new vehicles myself, but also didn't want just white cubes as vehicles. When I was looking for modelling help I still had the racing game Blur in mind as a visual inspiration, so when two members of my local community reached out to help, my request was for a more realistically modeled car. <a href="https://ilustrawes.itch.io/">Wesley</a> and <a href="https://www.artstation.com/paulohncostaart">Paulo</a> did amazing work, maybe too amazing, and now my poor decision-making lead me to a PS2 quality model in a world of white cubes...

In the end, some more experienced contacts advised me to use only free assets for the prototype as its purpose is solely the implementation of car and race systems, and leave non-essential graphics for an actual game. I ended up following their word, and instead used the rally car models from <a href="https://assetstore.unity.com/publishers/52093">Ash Dev</a> (the earlier artists were ok with this). I then finalized some menus and picked some stock photos from Unsplash and it was ready to post online.

## Second Playtest

The day had come. This time I was in town and the event was bigger than usual, being the last for the year, some 20 attendees. I was excited and a bit tense, I don't usually show my work to so many people. Before setting up the test PCs I actually got to talk to some new faces about my project and some of the challeges above, and that's always great. I also got to test games from my colleagues, give feedback and even help fix some bugs on the fly.

<div class="col mt-6">
    <div class="row-sm mt-1 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-5.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="row-sm mt-1 mt-md-0">
        {% include figure.html path="assets/img/devlogs/making-project-nitro-6.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">If you ever go to an event like this, I highly recommend a small notebook to write down all the feedback.</div>

While I didn't get much constructive feedback on issues (people actually understood the assets were unpolished on purpose), everyone seemed to approve the controls, and had nice words about the camera work and handling. I did my job, the car was fun to control and felt fast. Sadly the venue had to close earlier than planned so people didn't get time to replay it for fun. What a bummer.

I did take some notes when guiding and watching the players, though. It wasn't obvious to me until that moment but, even though the drift system is a spitting image of the one in Mario Kart, both the fact the cars don't look like karts or cartoony in general and the drift doesn't spark like the one in the Nintendo game, so the connection wasn't immediate to some players and they took some slower laps while I explained drift-boosts to them. Fortunately, everyone got the hang of it by the second or third go-round.

Also, even though I made three cars with different driving styles, unless you're a car guy and know your Group Bs and your Lancia Deltas, their strengths weren't immediately apparent by their design, so instead of adding some flavor text for each car or some driving stats by their side, I just had to explain why "this one drifts kinda funky". I should probably patch this in soon.

## Closing Thoughts

I'm glad I made Project Nitro. There were many learning opportunities throughout those two months, and it's probably the first time I had playtesting as a major part of my project calendar. It was also great just _finishing_ something in a good while, last time I made a nice and packaged project to share was Lotus and Lyric back in February.

The dream of making a racing game is ever closer, but there's still lots of work to do to get there. AI drivers, track layout, art direction, progression, user interface, multiplayer, these are some of the aspects that still require research from my end. I'll also need to learn how to better manage a team of artists and contributors as I'll likely not be able to do every single facet of the game myself, as much as I wanted to.

Project Nitro now exists. I can fork it if I need to make another racing game. I will wait a bit more before picking it up again, though.