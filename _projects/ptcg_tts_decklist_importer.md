---
layout: page
title: PTCG importer for TTS
description: turns pokémon decklists into Tabletop Simulator objects
img: assets/img/projects/ptcgtts_thumb.jpeg
importance: 1 # use this for sorting
category: apps
---

<div class="text-center">
    {% include figure.html path="assets/img/projects/ptcgtts_image_2.jpeg" title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>

## About the Project

This is a project I made with my friend Thomaz through the course of a weekend, inspired by another friend of ours having problems with
the existing mods for Tabletop Simulator to get Pokémon cards from decklists.
After finding out <a href="https://github.com/jeandeaual/tts-deckconverter">an external tool</a> to do that task already existed but was outdated and no longer worked, we investigated making such a tool ourselves, and here we are.

## Features
- Supports cards from Black and White onwards, including cards after Scarlet and Violet
- Compatible with decklists from: pokemoncard.io / limitlesstcg.com / ligapokemon.com.br

##### GUI:
- Exports json files to be opened as TTS saved objects
- Cards from the json have a transcript of the original card in their description
- Supports custom card backs to emulate card sleeves

##### Python Script:
- Also exports images to be used in TTS custom decks
- Can be set up with an API KEY from PokemonTCG.io to build decks faster.

## Development Tools

The app is made in Python, using Custom TKinter for the interface and Pyinstaller for packaging the executable.

The PokemonTCG.io API can be interacted with solely with HTTPS requests 
but they also have a dedicated "sdk" package for Python, <a href="https://github.com/PokemonTCG/pokemon-tcg-sdk-python">found here.</a>

### Development Process

From idea to working version, my friend and I only took 3 days. Splitting tasks effectively and prototyping each step with placeholders helped us get to a working prototype quickly.

<!-- You can read more about the process in <a href="">a dedicated blog post I wrote on it.</a> -->

### Future Plans

I want to make the app a bit more user friendly to those who can't use Python, hence the GUI, but features like automatically creating files on TTS's vault folder or adding images to the saved objects would be nice.

## Gallery

<div class="text-center">
    {% include figure.html path="assets/img/projects/ptcgtts_image_3.png" title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">Very simple and functional user interface</div>

<div class="text-center">
    {% include figure.html path="assets/img/projects/ptcgtts_image_1.jpeg" title="" class="post-img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">Example of card sheet made by the app (currently only made via python).</div>

## Download

The source code and executable release are available in <a href="https://github.com/NatePlays95/ptcg-tts-decklist-importer">this Github repository.</a>