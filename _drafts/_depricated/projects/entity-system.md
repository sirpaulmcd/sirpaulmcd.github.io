---
layout: default
title: Entity System
permalink: /projects/onion-trail/entity-system
parent: Onion Trail
grand_parent: Projects
has_children: false
nav_order: 1
nav_exclude: false
has_toc: false
---

# Entity System

The entity system is responsible for handling the controls, health, and status effects of player/NPC entitites. This system is still under development at the moment but the overall layout looks somewhat like this:

<p align="center">
    <img src="/assets/images/onion-trail/entity-system/base-infrastructure.png" alt="entity system base infrastructure" />
    <br />
    Base infrastructure
</p>

## Controller Subsystem (green)

This system contains the infrastructure for controlling player and NPC entities. All entities have common properties like movement speeds and rigidbodies. Player entities are controlled using keyboard/gamepad while NPC entities are controlled using finite state machines to simulate intelligent behaviour:

<p align="center">
    <img src="/assets/images/onion-trail/entity-system/base-enemy.gif" alt="base enemy AI preview" />
    <br />
    Simple enemy AI using finite state machine (FSM)
</p>

## Stat Subsystem (blue)

This system contains the infrastructure for inflicting status effects on entities. Status effects can be placed on an entity to manipulate their controls, health, appearance, etc. The Stat system works with the WarAndPeace system to induce knockback effects on attacked entities. Here's an example status effect that allows entities to catch on fire. If they run into other entities, the fire will spread:

<p align="center">
    <img src="/assets/images/onion-trail/entity-system/combustion.gif" alt="combustion status effect preview" />
    <br />
    Combustion status effect
</p>

## Health Subsystem (red)

This system contains the infrastructure that allows entities to be healed, take damage, and die. Changes in health can be visualized through health bars and damage pop-ups as seen above.
