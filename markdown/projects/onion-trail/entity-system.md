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

The entity system is responsible for handling the controls, health, and status effects of player and NPC entitites. It is a bit of a work-in-progress at the moment but the overall layout looks somewhat like this:

<p align="center">
    <img src="/assets/images/onion-trail/entity-system/base-infrastructure.png" alt="entity system base infrastructure" />
    <br />
    Base infrastructure
</p>

## Controller Subsystem (green)

This system contains the infrastructure for controller player and NPC entities. All entities have common traits like movement speeds and rigidbodies. Player entities are controlled by a person using either keyboard or gamepad. NPC entities are controlled using finite state machines to simulate intelligent behaviour:

<p align="center">
    <img src="/assets/images/onion-trail/entity-system/base-enemy.gif" alt="base enemy AI preview" />
    <br />
    Simple enemy AI using finite state machine (FSM)
</p>

## Stat Subsystem (blue)

This system contains the infrastructure for status effects of entities. Status effects are any effects placed on an entity that manipulate controls, health, appearance, etc. Knockback effects are handled differently between players and AI because they are controlled by different means. Here's an example status effect that allows entities to catch on fire. If they run into other entities, the fire will spread:

<p align="center">
    <img src="/assets/images/onion-trail/entity-system/combustion.gif" alt="combustion status effect preview" />
    <br />
    Combustion status effect
</p>

## Health Subsystem (red)

Infrastructure for player health. This system allows the player to be healed, take damage, and die. Changes in health are reflected in applicable health bars and damage numbers pop up on the screen as seen above.
