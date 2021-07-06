---
layout: default
title: Onion Trail
permalink: /projects/onion-trail/
parent: Projects
# grand_parent: Blog
has_children: true
nav_order: 2
nav_exclude: false
has_toc: false
---

# Onion Trail

I am the team lead for a cooperative party revamp of the classic game [Oregon Trail](<https://en.wikipedia.org/wiki/The_Oregon_Trail_(1985_video_game)>) similar in nature to [Death Road to Canada](https://store.steampowered.com/app/252610/Death_Road_to_Canada/).
The game is currently being developed in C# using the Unity game engine using an agile development approach.
All scripts are open source.
For more info, check out the [project wiki](https://github.com/sirpaulmcd/Onion-Trail-Open/wiki).

<p align="center">
    <img src="/assets/images/onion-trail/miscellaneous/elite-gardener.png" alt="elite-gardener.png" width=200px/>
</p>

I have made many contributions to the game. My most impressive of my contributions are:

- [Entity system](/projects/onion-trail/entity-system): Software architecture for managing the controls, health, and status effects of player and NPC entities.
- [Oregon Trail system](/projects/onion-trail/oregon-trail-system): Game mechanics for performing Oregon Trail style vehicle travel, prompts, and resource management.
- [WarAndPeace system](/projects/onion-trail/war-and-peace-system): A generic software architecture for implementing a variety of weapons, obstacles, and items in the Unity game engine.
- [Wave Survival system](/projects/onion-trail/wave-survival-system): A wave survival game mode where waves can be designed entirely through the inspector.

I also have some small-scale [miscellaneous](/projects/onion-trail/miscellaneous) features to show off. As a teaser, here's an example weapon implemented using the WarAndPeace system. A projectile launcher that shoots self-regulating bullets that can:

- Deal damage with critical chance
- Apply knockback through impulsive forces or velocity changes
- Pierce through a specific number of targets
- Ricochet off of walls a specific number of times

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/bullet-launcher-1.gif" alt="bullet-launcher-preview.gif" width=350 />
    <img src="/assets/images/onion-trail/war-and-peace-system/bullet-launcher-2.gif" alt="ricochet-preview.gif" width=257 />
    <br />
</p>

Intrigued? If so, there's plenty more gifs of weapon implementations on the [system description page](/projects/onion-trail/wareandpeace-system).
I also go into detail about the system architecture.
