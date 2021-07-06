---
layout: default
title: Oregon Trail System
permalink: /projects/onion-trail/oregon-trail-system
parent: Onion Trail
grand_parent: Projects
has_children: false
nav_order: 2
nav_exclude: false
has_toc: false
---

# Oregon Trail System

Onion Trail is partly inspired by a classic video game called Oregon Trial. In Oregon Trail, you travel on a wagon and respond to text prompts that influence your resources. If you run out of resources, you die and the game ends. Onion Trail is planned to have a similar overall game mechanic.

## Travel and Prompts

In Onion Trail, players will travel from point A to B on a tractor. While they are traveling, they will be faced with prompts and events that manipulate their resources. Many prompts take place inside the vehicle. However, some prompts require the player to leave the vehicle and beat a level. Here's a silly example:

<p align="center">
<img src="/assets/images/onion-trail/oregon-trail-system/basic-prompts.gif" alt="Road travel and prompt preview" />
<br>
Road travel and prompts
</p>

The prompt system was designed with game designers in mind. New prompts can be created and set up entirely through Unity's inspector rather than having to edit code.

## Resources

Resources can either be gained through in-vehicle prompts or picked up when outside the vehicle:

<p align="center">
<img src="/assets/images/onion-trail/oregon-trail-system/resources-1.gif" alt="walk over resources preview" />
<br>
Walk-over resources
</p>

Other resources are too large and substantial to pick up as you go. In these cases, the resource needs to be lifted and carried to the vehicle:

<p align="center">
<img src="/assets/images/onion-trail/oregon-trail-system/resources-2.gif" alt="lift and carry resources preview" />
<br>
Lift and carry resources
</p>
