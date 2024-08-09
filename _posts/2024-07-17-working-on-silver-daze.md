---
layout: post
title: Working on Silver Daze
date: 2024-08-09
#description: an example of a blog post with table of contents
tags: devlog
related_posts: false
toc:
  beginning: true

---

<div class="row mt-3">
    <div class="col-2 mt-3 mt-md-0"></div>
    <div class="col-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/silverdaze_cover.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-2 mt-3 mt-md-0"></div>
</div>

### What's a "Silver Daze"?
_Silver Daze_ is a JRPG-style game with heavy influence from 2000s aesthetics in anime, retro games, music and setting.
It's a game about growing up into adulthood, letting things go, and supporting your friends. It also has really cool
combat mechanics focused on customization and player expression as character fight with magical Cards which can be swapped and traded.

Pitch aside, Silver Daze is a project headed by Sawyer Friend (yes that's his surname), developed in RPGMaker and featuring a handful
other team members, which includes myself!. This is probably the first Steam Game that I've been involved with from the start, which
isn't a big accomplishment but did have me learning details about making Steam builds, achievements, marketing etc.

### My role on the team
Sawyer likes to work autonomously as planning for other members that might leave the team for whatever reason is not ideal to him, 
which does make his projects have a very "solo-dev" vibe, one Game Director person with a very strong vision for the game, 
handling writing, mapping, art, combat balancing and half of the game's soundtrack, with Graves(RetroReaper) covering the other half. 
Still, there are things he can't do but I can.

My main contributions are for more technical, code-related features that serve as either QoL or improvements on systems and visuals we had on paper.
For example, I made code to transfer save data from Axial - Disc 1 into Axial - Disc 2 and we're using similar code to get demo saves into
the main game without the player having to mess with the files. Similarly, we're planning on giving the player special cards if they're playing on
Steam and have save data for games from other dev friends of ours, like 
<a href="https://store.steampowered.com/app/886200/EndCycle_VS/">Endcycle VS</a> and 
<a href="https://store.steampowered.com/app/1248840/Sephonie/">Sephonie</a>. 
I also implemented some of the first custom UI elements and menus we had (battle UI, card binder menu), then taught Sawyer the very basics 
of how to make his own edits to other screens, which lets our game stand out from other RPGMaker games a bit more. I'm also there to unscrew
any bugs he creates by messing with the code himself.

<div class="text-center">
    {% include figure.html path="assets/img/devlogs/working-silverdaze-binder.png" title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">There are hundreds of cards to collect!</div>

I'm also responsible for a handful of visual effects throughout the game that didn't have community solutions at the time. I made the "shaders"
for what we call _Foil_ enemies, a rare modifier enemies can have that makes them drop special rare foil cards, inspired by shiny hunting in Pokémon; 
There are other visual modifiers for some secret enemies further in the game I'll keep hidden for now. There are also popup messages for when passive
and trigger states activate, something I really enjoyed from Fire Emblem and wanted an excuse to replicate.

<div class="row mt-3">
    <div class="col-2 mt-3 mt-md-0"></div>
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include video.html path="assets/video/devlogs/working-silver-daze-foils.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true loop=true %}
    </div>
    <div class="col-2 mt-3 mt-md-0"></div>
</div>
<div class="caption">Chances of finding these are pretty low.</div>

Outside of that, I'm also present for a few brainstorming sessions where Sawyer metaphorically sits down on any random channel on our dev Discord server
and starts throwing ideas for next story chapters or card mechanics and me, Nedben and Royal can join and give opinions or new ideas.
Overall, as I have a more supportive role the workload is very light and doesn't encroach time from my other endeavors.

### Marketing adventure
Many of Sawyer's friends incentivized him to sell Silver Daze on Steam as we guessed the fact his last project, Axial, was free, Steam wouldn't push it
as strongly in the algorithm. He eventually caved in and we even had a little game marketing study group going on. Alongside that I also got to show
early builds to a few friends to gather some basic feedback, which was pretty fun.

Then, a surprise hit my inbox: the game developer showcase in this local, bi-yearly anime convention in my city didn't have enough applicants so the organizer
politely asked the community if they wanted to join. I dismissed it at first as I had just finished 
<a href="{{ site.url }}{{ site.baseurl }}/blog/2024/working-on-fishfolk-drifty/"> working on Fish Folk - Drifty </a> and had no other projects in the pipeline, 
but then a friend told me I should take Silver Daze to the venue as I was technically a dev and nobody could contest that.
I checked with Sawyer, he gave me his OK, then I went to design and print a poster and a few pamphlets 
(something the other devs at the con forgot to do until I showed up packed with pretty posters).

<div class="col mt-3">
    <div class="row-3 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/working_silverdaze_con_1.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="row-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/working_silverdaze_con_2.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="row-3 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/working_silverdaze_con_3.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">The convention had me a bit anxious but I pulled through!</div>

I spent Friday and Saturday at the venue, meeting fellow devs, playtesting their games, as well as receiving and discussing with strangers about Silver Daze
and the games market in Brazil in general. I made sure to borrow a set of headphones as Sawyer and Graves put a lot of care into the soundtrack and I wanted
at the very least the title screen and boss songs to be heard. I also distributed a total of 30 pamphlets, rookie numbers compared to another experienced dev
I met but definitely a good start.

For results... We got 8 wishlists the entire weekend 🤡

It was the first convention I attended as a dev, and I did learn a lot of stuff. With a game that sells itself on nostalgia and
older aesthetics as much as it sells itself on its own merits, my target audience shows up around the dev venue around late afternoon, while school kids
who mostly play on phones are the visitors during the morning. I, of course, stayed my first and second days in the morning and early afternoon, and took
the late afternoon for my own break. I wanted to do it correctly on the Sunday but I got sick the midnight before, so I couldn't really test that hypothesis.
I'm sure all the pamphlets did help our wishlist rates not fall all the way to zero for a few weeks. I hope so.

The event still had me left a few dozen pamphlets and a handful of posters, so I put the posters up around specific blocks in my university I knew had 
students that match our target audience (so, computer science, digital arts and games courses), as well as giving the pamphlets to a dozen friends.

### We have a demo!
Yeah, uh, due diligence from a dev team member and all, we're launching Silver Daze's public demo on August the 10th! 
It will be available on both Steam and Itch.io, and we plan on hosting it on Newgrounds too. You can play the browser builds on your phone as well.
If a retro JRPG with teens and cool card battles sounds interesting please check it out!

<a href="https://store.steampowered.com/app/3097590/Silver_Daze_Demo/">Link to demo on Steam</a>
<!-- <a href="https://store.steampowered.com/app/3097590/Silver_Daze_Demo/">Link to Itch.io</a> -->