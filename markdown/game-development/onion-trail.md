---
layout: default
title: Onion Trail
permalink: /game-development/onion-trail/
parent: Game Development
# grand_parent: Blog
has_children: true
nav_order: 2
nav_exclude: false
has_toc: false
---

# Onion Trail

<p align="center">
    <img src="/assets/images/onion-trail/miscellaneous/elite-gardener.png" alt="elite-gardener.png" width=200px/>
</p>

Back when I was a student, I lead a small team of programmers and artists to prototype an idea I had. Onion Trail is a cooperative party revamp of the classic game [Oregon Trail](<https://en.wikipedia.org/wiki/The_Oregon_Trail_(1985_video_game)>) similar in nature to [Death Road to Canada](https://store.steampowered.com/app/252610/Death_Road_to_Canada/). Like Oregon Trail, the purpose of the game is to survive a road trip by managing resources. If any particular resource depleats, the players are at a high risk of death. However, in this game, players routinely left the vehicle to move around in 3D space. For example, combat encounters, minigames, and pit stops would have the players walking around and interacting with the world. The story involved the world being overwhelmed by plant overgrowth and an unlikely team of gardeners had to save the day. I implemented a playground of game mechanics:

## Oregon Trail Road Trip Mechanics
Much like Oregon Trail, the players travelled in a vehicle. In this case, a tractor. They managed the resources of food, fuel, and medicine. If the players ran out of any particular resource, they became likely to die by random encounter along the trip. Here's an example of what a random encounter looked like.

<p align="center">
  <img src="/assets/images/onion-trail/oregon-trail-system/basic-prompts.gif" alt="Road travel and prompt preview" width="600" />
</p>

When outside of the vehicle, players could find resources that would bolster their chances of surviving the trip. Small quantities or resources were collected by walking over them while large quantities had to be carried back to the vehicle.

<p align="center">
  <img src="/assets/images/onion-trail/oregon-trail-system/resources-1.gif" alt="walk over resources preview" width="300" />
  <img src="/assets/images/onion-trail/oregon-trail-system/resources-2.gif" alt="lift and carry resources preview" width="400" />
</p>

Players could also lift/throw each other or objects in the scene in order to reach new heights and solve puzzles. Stacked players were bound together and acted like a stiff spring when walking into obstacles.

<p align="center">
  <img src="/assets/images/onion-trail/lifting-system/stacking-preview.gif" alt="player stacking preview" width="300" />
  <img src="/assets/images/onion-trail/lifting-system/stack-collisions.gif" alt="collisions carried down stack preview" width="400" />
</p>

Some environments were large enough that players could enter buildings.

<p align="center">
  <img src="/assets/images/onion-trail/miscellaneous/building-interior.gif" alt="building interior preview" width="600" />
</p>

Players could also interact with objects in the scene and talk to NPCs.

<p align="center">
  <img src="/assets/images/onion-trail/interactable-system/door-interaction-preview.gif" alt="door intearction preview" width="300" />
  <img src="/assets/images/onion-trail/dialogue-system/dialogue-preview.gif" alt="dialogue preview" width="369" />
</p>

## Combat Mechanics
There were supposed to be a variety of combat encounters in the game so I implemented an extensive combat system that supported status effects, piercing, critical chance, and knockback. I used this system to create a large variety of weapon types. For example, melee combat and grenades.

<p align="center">
  <img src="/assets/images/onion-trail/war-and-peace-system/melee-weapon-preview.gif" alt="melee weapon preview" width="325"/>
    <img src="/assets/images/onion-trail/war-and-peace-system/grenade.gif" alt="grenade preview" width="350" />
</p>

I also made hitscan and projectile bullets. The projectile bullets were capable of ricocheting off of walls.

<p align="center">
  <img src="/assets/images/onion-trail/war-and-peace-system/bullet-launcher-1.gif" alt="bullets preview" width=350 />
  <img src="/assets/images/onion-trail/war-and-peace-system/bullet-launcher-2.gif" alt="ricocheting bullets preview" width=257 />
</p>

The combat system was designed to be used by players but also by enemy AI. Here's a simple AI attacking the player with a melee weapon.

<p align="center">
  <img src="/assets/images/onion-trail/entity-system/base-enemy.gif" alt="base enemy AI preview" width="600" />
</p>

One random encounter involved surviving multiple waves of enemies.

<p align="center">
  <img src="/assets/images/onion-trail/war-and-peace-system/weaponUI.gif" alt="Wave survival and flamethrower preview" width="600" />
</p>

As seen by the flamethrower in the above gif, status effects could be induced on characters. If a player was ignited, they'd start to run and were unable to stop. If they bumped into another player, the other player would also begin combusting.  

<p align="center">
  <img src="/assets/images/onion-trail/entity-system/combustion.gif" alt="combustion status effect preview" width="600" />
</p>

When a player ran out of health, they'd become incapacitated and could be revived by a teammate. If there were no other living players to save them, they'd instantly die.

<p align="center">
  <img src="/assets/images/onion-trail/life-and-respawn-system/incapacitation-2.gif" alt="incapacitation preview" width="400" />
  <img src="/assets/images/onion-trail/war-and-peace-system/spikes-preview.gif" alt="spikes preview" width="300" />
</p>

When I worked on this project, I was a software engineering student just dabbling with the idea of becoming a game developer. My design was a bit too undefined and ambitious for a small team with no professional experience to achieve in their spare time. Regardless, it was a great time to tinker and learn. Work on the project stopped after I got my first game development job. I may come back to this project if I flesh out a design document and believe the idea is worth pursuing again.