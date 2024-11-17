---
layout: page
title: PokeData App
description: a mobile pokedéx app
img: assets/img/projects/pokedata_app_thumb.jpg
importance: 1
category: apps
---
<!-- 
<div class="text-center">
    {% include video.html path="assets/video/projects/projectnitro_preview.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
</div> -->

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/pokedata_app_1.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/pokedata_app_2.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/pokedata_app_3.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">Screenshots from the app.</div>


## About the Project

A Pokédex-like app made in Godot 4 targeting android devices. This was made as a learning exercise for Godot UI and HTTP Requests.

#### Features

- Up-to-date data for Pokémon species and abilities provided by PokeAPI; 
- Sleek and responsive user interface;
- Support for touch, swipe and mouse operation.

## Development Tools

The prototype was made in Godot 4.2, using Android Studio to help with builds and testing.
All the data currently is sourced from <a href="https://pokeapi.co/">PokeAPI</a>, a free and mostly up-to-date RESTful API.

## Project Details

<!-- Here, you can go into more depth about your game development project. Talk about the inspiration behind the game, challenges faced during development, and any interesting anecdotes or stories related to the project.  -->

<!-- ## Development Process -->

<!-- Describe the step-by-step process you followed during development. This could include brainstorming, prototyping, coding, testing, and refining the game mechanics. -->

#### Challenges and Solutions

A lot of the problems I faced were related to memory management. Turns out, instancing a literal thousand nodes in a list, each with its own _image_ and _JSON dictionary_ is not great for both RAM and VRAM. 

Originally, it would try to load in sections of 200 monsters at a time all at once, which meant ~600 HTTP GET requests as well as loading 200 720x720 images onto VRAM. Godot can't handle all those requests all at once, so it freezes and crashes. Even reducing the number of requests means some images simply don't load. To adress that, I had to make a faux Infinite Scrolling Container that only loads a few dozen pokémon at a time, requesting more if you scroll to the bottom.

For the images, I decided the search screen should use lower resolution 96x96 pixel sprites for the search screen instead of HD art. That saves on some VRAM. I left the full artwork for the individual pokédex screen of each monster. I also considered making the images not visible when the scene is stored in the stack, but while that helps the graphics card, the images stay loaded so that didn't help.

As for RAM usage, the final search "only" consumes 600MB if you scroll and load all the 1000 pokémon, running around 200MB under normal use. It seems memory isn't properly cleared by the garbage collector either. It was originally even heavier as requesting data such as pokemon types for each species required requesting everything else for that species (PokéAPI has no query parameters outside of ``limit``), so I simply ignored that for now.

<!-- While I thoroughly enjoy working with Godot, there are still some issues with both physics and graphics that are hard to ignore.
Project Nitro's vehicle simulation has plenty of workarounds for bugs in the engine that I'm not quite as qualified to fix and fork the source myself.

I also found prototyping difficult without doing the suggested workflow of modelling in Blender first, then exporting to Godot, instead of using the engine's CSG nodes. I did it anyway as I'm not a Blender expert by any means and with my low free-time it would take me a month to make a handful of tracks. -->

#### Future Plans

I want to further improve this project on a later date, focusing more on the performance part than the features part. ~500MB of RAM is not ideal for what's supposed to be an alternative to _searching on Google_. 

I need to look into caching the requests into local storage, as each pokemon is only a few hundred kilobytes in size. Caching would also help with all the times I want to display a pokémon alongside one or two datapoints like type or region or abilities, as well as make queries myself as PokéAPI doesn't support them. Everyone else working with the api also recommended to cache all the pokémon so it should be ok.

But yes, more features would be nice. Being able to search through all the items and moves or seeing alternative forms like megas would improve the usability. I could also study how to change between light and dark themes or how to add support for other languages, which PokéAPI also has.


## Gallery
<br>

<div class="text-center">
    {% include video.html path="assets/video/projects/pokedata_app_preview.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false loop=false %}
</div>
<div class="caption">Demonstration for the app's infinite scroll and scene stack.</div>

<div class="text-center">
    {% include video.html path="assets/video/projects/pokedata_app_search.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false loop=false %}
</div>
<div class="caption">You can search pokémon up to Gen 9 by name.</div>

## Download

You can find PokéData App's source code in <a href="https://github.com/natanmaia95/PokeDataApp">this Github repository</a>.