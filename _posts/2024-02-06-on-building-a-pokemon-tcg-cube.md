---
layout: post
title: On building a Pokémon TCG Cube 
date: 2024-02-05
#description: an example of a blog post with table of contents
tags: tcg
related_posts: false
---

<div class="row mt-3">
     <div class="col-2 mt-3 mt-md-0"></div>
    <div class="col-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/fotocubo1.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
     <div class="col-2 mt-3 mt-md-0"></div>
</div>

I've been on a Pokémon TCG craze for almost a year now, both as a way to bond with my friends, as well as to satisfy my
"strategy-game" neurons with something a little more physical. My project for last year was building a Cube for Cube Draft,
and today I wanna share a bit of how I got to build one and some of my design considerations.

I should first explain some terms for those unfamiliar with "cubes" in trading card games:

- Draft: A play format where instead of using pre-assembled decks, players open card packs or "boosters"
and have to build a deck from the random selection of cards they obtained, alongside some extras like resource cards.
Not only are there very peculiar rules for drafting cards with a group of people, but games like Magic the Gathering
have entire card sets built with the drafting or "Limited Format" experience in mind.

- Cube: from the MtG community, a "cube" is a collection of cards, usually over 300, stored in a container
for the purpose of building "homemade boosters" for a draft experience that doesn't require buying new boosters every time.
Cubes were initially made out of bulk cards from someone's collection but they can also be assembled very meticulously.

## How did I get here?

My journey with cubing started just after my first pre-release event for Pokémon TCG.
These work like a soft-drafting experience, with each player receiving two randomly-chosen half-decks from a set of four options,
as well as a handful of boosters for the "deckbuilding" part. So you could find an extra attacker or supporter for the deck you received,
or multiple cards of another color to pivot the deck into another direction, or even a powerful "rulebox" card that may help flip the scales
in a difficult matchup and ask you to change your deck to better support it.


<div class="row mt-3">
    <div class="col-3 mt-3 mt-md-0"></div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/prereleasereboot1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-3 mt-3 mt-md-0"></div>
</div>
<div class="caption">I finished the tournament in third place by the way!</div>

After that, though, I had a hundred cards, pokémon trainer and energy alike, that I didn't have any use for. I also had a few cards from opening
boosters so now my box of spare cards was really heavy. I wondered what to do with all those fun cards. I also really really wanted to play more
draft, but had used all my money for that month.

Then I found this video on drafting pokémon cards by TheJWittz.
<div class="embed-responsive embed-responsive-16by9">
    {% include video.html path="https://www.youtube.com/embed/_l9-FJZj3V0" class="img-fluid rounded  z-depth-1" %}
</div>
<div class="caption">I fell in love with cube draft.</div>

I watched videos on playing and even building cubes, for both MtG and Pokémon, and grew incredibly excited to have this
very "board game-y" experience of sitting down with friends for a few hours and playing something I had a hand in building.
As someone who loves making games and art and loves doing group activities that's the best thing I never thought I needed. 

I then got all the cards I had, bought a few more bulks from other players to get all the energy colors, and started assembling my own cube.
Month by month I expanded my collection, buying cards for the sole purpose of adding them to the cube and experimenting with them.
Cards that would hardly see any play elsewhere but could fit nicely in a cardset I have complete control of and can balance accordingly.
A few months later I finally got a group of friends to play the cube draft for the first time, and we had a lot of fun!

## My Design Process for the Cube

I ended up with a ~400 card cube, which supports up to 8 players. I wanted to include all the 11 types from pokémon's recent history, which meant including 
a very decent count of cards for each. Players build decks of 40 cards, with roughly 12 pokémon, so to support at least three players including any one
type in their decks as half their type support I'd need close to 20 pokémon. We do 3 boosters (sets of 15 random cards) at a time, with each booster
taking around 10 minutes to draft completely. I considered opening 4 boosters for better deckbuilding but so far I felt a fourth booster would
drag the building process for too long and leave less time for playing the decks.

At first I just picked enough cards of each type from my bulk, as well as very cheap supporter cards I bought from stores, just to complete 360 cards.
I then kept an eye for cool and unusual cards in other people's binders I could include in the cube. Cards like Charizard and Tyranitar
and Pikachu were included less because of their power and utility and more because there's this "fantasy" of battling with cool and
popular pokémon I wanted to capture. I made sure to include both cute and cool mons in each type, so that newer players could
discover new favorites and older players could have fresh experiences from other formats.

Then, as the cube started to take shape, I looked for very specific cards to better balance specific strategies or archetypes, like a few
Switch cards, mons that buy cards and accelerate energy, a few Cynthias and Pokémon Fan Clubs to add consistency to decks, and some
Super Rods and Energy Retrievals to extend deck life. Eventually some of the mons I got from my bulk went back to the bulk, and I did buy
many more cards I ended up not using, but at this point I'm way too invested to bother.

Buying a handful of cards every month wasn't a massive monetary investment or anything, and it meant I could continuously engage with building
the cube even after the hyperfixation had passed. Of course, I also did simulated drafts with myself and played casually with my cousins
before getting to what I'd consider a "balanced" state.

<div class="row mt-3">
    <div class="col-3 mt-3 mt-md-0"></div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/fotocubo3.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-3 mt-3 mt-md-0"></div>
</div>
<div class="caption">It's much harder to both balance and randomize 11 color attributes.</div>

#### Mutant Evolution

This rule allows any Stage1 mon to evolve from any Basic mon from the same type, same for Stage2 cards.
Normal Evolution rules still apply.
It was made to address how wonky and limiting the evolution rules for the TCG actually are for deckbuilding,
and helps the game feel more closely match the ones from MtG and in particular the new Digimon TCG, while
still including a variety of pokémon of each type. 
Otherwise, a three hundred card cube would only have two or three evo lines and that's boring.

Yes, this means you can evolve a Mewtwo into a Kirlia, or a Tynamo into an Electivire. It's a very interesting
rule that would be strongly abused in official formats, but it can be deliberate in a cube setting.
As such, I made sure each type had a good assortment of powerful Basic and Stage1 pokemon, one or two legendaries
(and a fair number of bad pokémon too haha).

#### Pokémon Proportions

Each pokémon type is represented by 24 monsters, with a spread of roughly 12 Basic, 9 Stage1 and 3 Stage2 cards.
It may feel unbalanced at first, with other cubes having less drastic proportions, but the Mutant Evolution rule
allows for very powerful cards in the Basic and Stage1 groups, so each type ends up having 8 or so chase cards,
as well as some neat support cards.

Roughly a third to half of the pokémon carry abilities, as a good amount of cards came from card bulk so of course
they wouldn't have useful abilities. It also gave me room to include interesting effects tied to pokémon moves,
like energy acceleration from deck, or switching out the opponent's active mon, or doing massive damage with added recoil.

Even with the spread biased towards basic pokémon, some players said they had really bad luck finding basics for their
initial evolution picks. I first assumed it was a mix of bad deckbuilding and bad booster luck, but a third factor I only
later noticed was how biased the type selection between players was. Three players started to chase Fairy cards for the
novelty of a now dead type, and the only decks running Fire and Water cards were newer players with less experience which 
ended up making decks with 4 energy types. 

#### Trainer Support

The recommended spread of trainers cards is roughly half the cube, so from 3 packs of 15 you potentially have ~22 trainers
to choose from to build a deck of 40 which should have roughly 10-15 trainers. From my last playsession though,
either I miscounted or the suffle was really unlucky but I felt a distinct lack of trainer cards from my picks. It's a fine balance;
too few and games feel unflexible and players stay stuck with bricked hands for too long, too many and players can't find
decent pokémon of their chase type in a sea of pokéballs and vitality bands and nurse joys. 

At first I was going to solely add generic and flexible trainers every deck could use like Switch and Boss's Orders, I felt games 
would end up too unpredictable due to trainers, and I'd like the surprises and gotcha moments to come from the mons themselves.
Still, I left some of those powerful trainers for keen-eyed veterans to look out for.

Instead, I included less "meta" cards for Standard but which could still be useful with the lower power level, like Energy Retrieval
or Pokémon Center Lady, which have come in handy in a few matches. I also included both type-specific support, trying to keep at least
3 or 4 cards including supporters, items and tools to help each type. There are also cards that see little to no use in constructed
pokémon tcg formats but can be played around with here, like cards to make both pokémon confused or cards to re-roll coin tosses
or cards to look at your opponent's hand.

Also, in a limited format without "big basic" rulebox mons and *very limited* options for switching out, strategies around Status Effects
are valid. I made sure to include a handful of mons with those effects, as well as tools and supporters to both apply and remove them easily.
There are also many pokémon and stadiums that deal more damage if the target has an effect, or increase the potency of that effect. 
Healing is also a valid strategy now, as health pools are smaller and attacks weaker, so I included heal supporters and items. 
Finally, the limited card pool means those powerful effects printed onto cards balanced by ending your turn early like Kiawe and Boost Shake
are actually usable, as turns tend to be slower from the lack of staple supporters and basic pokémon with powerful setup abilities.

#### Encouraging Type-mixing

Between having to support 11 entire types instead of the usual 5 or 6 attributes in other TCGs, and having to deal with multiple players
also chasing cards of the same type, players will inevitably end up making decks with at least two types. I personally think building around
3 basic energy types is the usual, 2 is an achievement and 4 is less than desirable. Having more types can help you escape out of unfavorable
weakness matchups as well as combine synergistic effects.

At least half the types have one pokémon with entirely colorless attack costs, and all have pokémon with many colorless costs in their attacks.
By making these costs achievable with any energy color, Pokémon makes these cards more "mixable" with other types, maybe to balance weaker attacks 
with versatility, or to incentivize using Special or Double colorless energy (a trick I also do, with as many as 6 double colorless in the cube so far).
There are still cards with no colorless costs; these are usually more powerful to combat the lesser flexibility both by their original design intention
and by my own selection.

Pokémon can also be mixable with their effects, by affecting pokémon outside their type. This is especially fun with Basic pokémon as they can then be included
in any deck and be useful with the only caveat being they may take the place of another basic that could be used for evolution. In counterpart,
pokémon with really powerful effects (like deck search, rain dance or healing) are usually limited to supporting only their own type, which is an interesting deckbuilding consideration.

<div class="row mt-3">
    <div class="col-1 mt-3 mt-md-0"></div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/en_US-Promo_SWSH-SWSH232-charmander.webp" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/sv1_en_031-1.webp" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/en_US-Promo_SWSH-SWSH221-cyndaquil.webp" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-1 mt-3 mt-md-0"></div>
</div>
<div class="caption">You can see how, despite having similar attacks, Charmander's effect is exclusive to fire types while Cyndaquil's can be used in any deck.</div>

Some cards can also encourage type mixing by design, either by adding extra effects if different energy is equipped like more damage or applying status,
or by interacting with effects their type is not normally associated with like fire types applying poison or using venoshock, or even by outright
requiring different energies to pay attack costs, like most Dragon-type mons. 

Also, Mutant Evolution introduces a fun flavor of mixing: cross-type evolution lines. I made sure to include many lines that change type when
evolving as if to encourage players to build around those types to have better consistency, like fairy azurill to water marill or grass scyther to
steel scizor or fire salandit to poison salazzle or dragon zweilous to dark hydreigon etc etc. Building a deck with both grass and metal cards means 
grass Scyther can be another valid path to your Stage2 metal Metagross, which is not only fun during deckbuilding but also a fun clutch play for you
and a surprise for your opponent. Having more colorless costs further helps cross-type evolution.

#### Power Balancing; including both Fairy and Dragon together

Even just looking at the Black/White cards and forward, there are major differences in power from 10 years of continuously making and selling new cards.
Where a Tyranitar from early 2010s would deal 150 damage with four or five energy, a Tyranitar from 2023 does 230 with only two energy.
While I made sure to give every type a similar distribution of new and old cards, with famously weaker types like fighting getting a helping hand,
and for the most part avoiding many 2023 cards, I didn't shy of including straight up worse and better cards inside a single type. 

<div class="row mt-3">
    <div class="col-2 mt-3 mt-md-0">
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/en_US-XY10-056-tyranitar.webp" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/sv2_en_135.webp" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-2 mt-3 mt-md-0">
    </div>

</div>
<div class="caption">I still included the old Tyranitar in the cube because its Raging Roar ability seems really hype and fun.</div>

I think part of building a draft experience is making obviously good cards to alleviate some choice paralysis 
and reward each good picks from boosters, and making bad cards that may afterwards get people thinking "can I still salvage this?..",
which is very much part of the fun in building your deck on the spot.

The Fairy type, even during its run, famously had low HP pools and lower attack power, instead focusing on support and healing,
situational effects even in this cube. Adressing it was simple enough, I made sure to pick the strongest fairy cards I could find, 
with Xerneas accelerating energy, Shiinotic searching other fairy mon, Togekiss doing mass healing, Florges decreasing attack costs 
(compensating for the weak attacks lol), and the infamous "Wages of Fluff" Whimsicott allowing the next attack to take extra prizes.

As for the Dragon type, it was completely absent in the TCG for the Sword and Shield era for almost two years, so there's a gap in power between
Sun and Moon dragons and Scarlet and Violet dragons. At first I wanted to include solely basic dragons with either full colorless costs
like Drampa or interesting abilities like Regidrago, as evolving into a different dragon with wildly different costs felt bad, but I then embraced 
the idea of dragon types as these "splashable" mons into two or three type decks, with powerful attacks as encouragement to build decks around
their type requirements.

Dragons are designed with the mindset of locking away powerful attacks with less consistent energy requirements, and I want to follow
this balance. While I did include Rainbow energy and Double Dragon energy, there are only one copy of each, as rare chase cards.
Dragon types from the Black and White and XY era were too weak for their energy costs, so I'm choosing the Stage2 cards from the newer sets as
you need to both evolve AND match the correct energy types. As such, it's the only type I didn't feel bad stacking very powerful cards from
Scarlet and Violet like Dragonite doing 180 damage with two energy: if a player drafts this card they might consider building a water+lightning
deck just to enable it, and I think that's fun.

<div class="row mt-3">
    <div class="col-2 mt-3 mt-md-0">
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/en_US-BW9-083-dragonite.webp" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/sv3-5_en_149_std.webp" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
        <div class="col-2 mt-3 mt-md-0">
    </div>
</div>
<div class="caption">Old dragon cards are not even worth including, I think.</div>

## Maintenance

I had close to 600 cards counting all the energy cards players have available to build the decks. As such, I needed some sort of container
to store and transport those cards, and card sleeves to both protect the cards and help with shuffling during playtime and re-sorting the collection.
Actually decent options for either of those would each ask me more money than I invested in the entire cube, so for now I cheaped out to get something playable.

For storage, I'm using a spare cardboard box from a pair of sandals we bought. Lucky me the cards are a very tight fit so they don't shake around
too much, and the box fits in my travel pouch neatly. It's just cardboard though, so I'm using elastic bands to hold it shut. For sleeves, I went with
those "penny sleves", cheap transparent sleeves sold in packs of 100 for 3 dollars or less. They're not all equally sized and some have funky finishing
at the edges, but they were affordable in bulk and both protect the foils well enough and make shuffling actually possible, so that's enough for now.

<div class="row mt-3">
     <div class="col-2 mt-3 mt-md-0"></div>
    <div class="col-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/posts/2024/fotocubo2.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
     <div class="col-2 mt-3 mt-md-0"></div>
</div>
<div class="caption">"Professionals have standards."</div>

As for shuffling the four-hundred or so cards to make boosters, I usually do it at home after a playsession (or after making tweaks), it's kinda relaxing.
Randomly shuffling a deck is simple enough, just cut and mash the cards together a few times, but this cube is the size
of 7 standard decks so that's a no-go. Luckily, I found 
<a href="https://nex3.medium.com/how-to-randomize-a-cube-8efc20bd87ae">this article by Natalie Weizenbaum</a> 
detailing how she tackles the problem.

In sum, first place all your cards in equally sized piles (I like to do 12 or 16 piles myself), which doesn't randomize the cards by itself,
but helps with the next step: thoroughly shuffle all the individual piles. Then stack those piles and repeat the process a few times.
Personally I feel it's random enough after 2 or 3 steps, but each step takes around 10 minutes at a lax pace. Funny enough, if you place an equal
amount of cards of each type in each pile, shuffling only once may actually lead to a less random but more balanced distribution of colors per booster. 
I still need to try that out, though.

## Final Thoughts

I wish there was a practical way to both make a cube-list for pokémon online and to export it for testing in, say, Tabletop Simulator.
At the time of writing I just discovered 
<a href="https://pokemoncard.io/cube/">the Cube Draft section in pokemoncard.io's website</a>, it's fairly hidden. It can't export to TTS but
there's a beta feature for drafting with friends from the browser and creating a decklist to use in something like LimitlessTCG. I might set a 
free weekend to port my physical cube to the website.

I've heard some people rent their Magic cubes for others to play, so I could look into that to kinda recoup my costs or invest in better storage, 
but for now I can barely even get my friends to play the cube, so asking them for both their time and money would feel really bad.
As I mentioned at the start, I like to treat the Cube draft similarly to a board gaming night with Munchkin or D&D oneshots or other games
that require a long time commitment and a close group of friends. Something I can use to spice an otherwise boring travel weekend or
downtime in an anime convention.