---
layout: default
title: Elite Gardening Squad
permalink: /projects/elite-gardening-squad/
parent: Projects
# grand_parent: Blog
has_children: false
nav_order: 3
nav_exclude: false
has_toc: false
---

# Elite-Gardening-Squad
I am the team lead for a proof-of-concept couch co-op dungeon crawler game about gardening.
As such, I hold weekly agile meetings to keep up to date with the team.
The game is currently being developed in C# using the Unity game engine. 
All scripts are open source.
For more info, check out the [project wiki](https://github.com/sirpaulmcd/Elite-Gardening-Squad-Open/wiki).

<p align="center">
    <img src="/assets/images/egs/miscellaneous/elite-gardener.png" alt="elite-gardener.png" width=200px/>
</p>
I have made many [contributions](https://github.com/sirpaulmcd/Elite-Gardening-Squad-Open/wiki/Paul-McDonald) to the game. 
The most impressive of my contributions is the [WarAndPeace System](https://github.com/sirpaulmcd/Elite-Gardening-Squad-Open/wiki/WarAndPeace-System) which is a generic software architecture for implementing a variety of weapons, obstacles, and items in the Unity game engine.

<p align="center">
    <img src="/assets/images/egs/war-and-peace-system/base-infrastructure.png" alt="base-infrastructure.png" />
    <br />
    Base Infrastructure
</p>
As a teaser, here's an example weapon implemented using the system.
A projectile launcher that shoots self-regulating bullets that can:

- Deal damage with critical chance
- Apply knockback through impulsive forces or velocity changes
- Pierce through a specific number of targets
- Ricochet off of walls a specific number of times

<p align="center">
    <img src="/assets/images/egs/war-and-peace-system/bullet-launcher-1.gif" alt="bullet-launcher-preview.gif" width=350 />
    <img src="/assets/images/egs/war-and-peace-system/bullet-launcher-2.gif" alt="ricochet-preview.gif" width=257 />
    <br />
</p>

Intrigued? If so, there's plenty more gifs of weapon implementations on the [system description page](https://github.com/sirpaulmcd/Elite-Gardening-Squad-Open/wiki/WarAndPeace-System). 
I also go into detail about the system architecture. 