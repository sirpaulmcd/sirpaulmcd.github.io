---
layout: default
title: Miscellaneous
permalink: /projects/onion-trail/miscellaneous
parent: Onion Trail
grand_parent: Projects
has_children: false
nav_order: 5
nav_exclude: false
has_toc: false
---

# Miscellaneous

This page is to show off miscellaneous features that don't need their own page.

## Building Interiors

Lately I've been experimenting with building interiors:

<p align="center">
<img src="/assets/images/onion-trail/miscellaneous/building-interior.gif" />
<br />
Building interior
</p>

## Interactable System

Upon pressing the "Interact" button, the player spherecasts in front of their position in search of GameObjects that inherit from the `IInteractable` interface. This allows the player to interact with NPCs, lift objects, and open doors:

<p align="center">
<img src="/assets/images/onion-trail/interactable-system/door-interaction-preview.gif" />
<br />
Door interaction
</p>

## Dialogue System:

Instantiates dialogue prefab to canvas when called. Allows for different fonts, text sizes, typing speeds, typing sounds. Allows players to skip the typing sequence.

<p align="center">
<img src="/assets/images/onion-trail/dialogue-system/dialogue-preview.gif" />
<br>
The dialogue system allows players to talk to NPCs in a traditional way
</p>

# Lifting System

The lifting system allows players to lift, throw, and drop certain objects.

Lifting mechanics:

- Lifters
  - Cannot do other actions (i.e. interacting or attacking) while lifting
  - Can throw what they are holding at any time
- Lifted
  - Can do other actions
  - Cannot immediately escape from their lifter (must wiggle off)
  - Cannot control their fall when thrown

<p align="center">
<img src="/assets/images/onion-trail/lifting-system/lift-carry-throw-preview.gif" />
<br>
Players can lift, carry, and throw
</p>

<p align="center">
<img src="/assets/images/onion-trail/lifting-system/stacking-preview.gif" />
<br>
Players can stack on top of each other strategically
</p>

<p align="center">
<img src="/assets/images/onion-trail/lifting-system/stack-collisions.gif" />
<br>
Collisions are carried down the stack
</p>

## Life and Respawn System

### Squad lives

<p align="center">
<img src="/assets/images/onion-trail/life-and-respawn-system/checkpoint-preview.gif" />
</p>

- Players share a set of lives. Lives only decrement when all players die.
- Dead players can be respawned by living players by touching a checkpoint for the first time.
- When a squad dies, a squad life is lost and the team respawns at the latest checkpoint.
- When the squad runs out of lives, the game is over.

### Incapacitation

<p align="center">
<img src="/assets/images/onion-trail/life-and-respawn-system/incapacitation-1.gif" />
<img src="/assets/images/onion-trail/life-and-respawn-system/incapacitation-2.gif" />
</p>

- Players that drop to zero health become incapacitated for a short period of time before dying.
- Incapacitated players are paralyzed and must wait for assistance.
- Incapacitated players can be revived through lifting. If neglected, they die.

### Ledge Respawning

<p align="center">
<img src="/assets/images/onion-trail/life-and-respawn-system/ledge-respawning.gif" />
</p>

- Players that fall off of the map are respawned onto the last piece of stable ground they have touched.
- Pit respawn locations are updated periodically.

## Carry Ridibody System

This system allows certain objects to carry other objects around without the use of friction. Allows pairing via external triggers or OnCollisionEnter (pairs on all sides, magnetic feel)

<p align="center">
<img src="/assets/images/onion-trail/miscellaneous/carry-rigidbody-1.gif" alt="preview without carry rigidbody system" />
<br>
Without CarryRigidbody system
</p>

<p align="center">
<img src="/assets/images/onion-trail/miscellaneous/carry-rigidbody-2.gif" alt="preview with carry rigidbody system" />
<br>
With CarryRigidbody system
</p>
