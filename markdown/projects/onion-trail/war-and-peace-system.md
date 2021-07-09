---
layout: default
title: WarAndPeace System
permalink: /projects/onion-trail/war-and-peace-system
parent: Onion Trail
grand_parent: Projects
has_children: false
nav_order: 3
nav_exclude: false
has_toc: false
---

# WarAndPeace System

The WarAndPeace system is a generic software architecture for implementing a variety of weapons, obstacles, and items in the Unity game engine.
Since healing is fundamentally the same as dealing damage, it works alongside the Entity system to lower _or raise_ health points.

## Infrastructure Layout

The classes that make up the WarAndPeace infrastructure can be seen in the image below.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/base-infrastructure.png" />
</p>

All weapon, obstacle, and item implementations simply inherit from these abstract classes and interfaces.

## Terminology

### Weaponized GameObjects (WGOs)

Any GameObject that is expected to deal damage/healing.
A WGO calculates damage/healing magnitude based on several parameters.
The magnitude is randomly selected between the minimum/maximum damage values.
The critical chance determines whether this magnitude will be multiplied by the critical factor.
If "friendly fire" is toggled, the weapon will hurt GameObjects of the same tag as the attacker.
In addition to damaging/healing, a weaponized GameObject can also apply knockback effects from the specified origin.
A desirable knockback origin changes depending on the implementation.
For example, the knockback origin of a bullet should be the bullet itself whereas the knockback origin of a melee weapon should be the attacker.

### Dynamic Weaponized GameObjects (DWGOs)

Instances of WGOs that are dynamically spawned, move through space, and interact with GameObjects that touch their colliders.
DWGOs are self regulating projectiles.
After being spawned into a scene and initialized by their corresponding weapon, they are responsible for themselves
and self destruct after a designated amount of time unless otherwise specified.
It is important to note that all DWGOs (i.e. projectiles) should be placed on the "Ignore Raycast" layer to avoid complications.

Additionally, the `ATriggerDWGO` and `AColliderDWGO` abstract classes may appear to share much of the same code.
This is necessary because `ATriggerDWGO` uses `OnTriggerEnter()` (yields a **Collider** argument) whereas
`AColliderDWGO` uses `OnCollisionEnter()` (yields a **Collision** argument).
Since the `OnXEnter()` methods yield different collision related arguments, the code cannot be shared.

#### Trigger DWGOs

Instances of DWGOs that use trigger colliders and interact with GameObjects via `MonoBehaviour.OnTriggerEnter()`.
Trigger DWGOs are used when the projectile is expected to pass through other GameObjects.
As such, these objects _typically_ neglect the physics system and calculate their own trajectories.
For example, a bullet may be expected to pass through multiple enemies without bouncing off and changing direction.
The same could be said for a melee weapon.

In some cases, you may want a Trigger DWGO that travels through some objects but reflects off of others.
For instance, a bullet that travels through enemies but ricochets off of walls.
In these situations, ricocheting can be simulated using methods such as raycasting (see bullet implementation).
Additionally, fast moving Trigger DWGOs can pass the transform of their targets before a collision is registered.
As a result, the induced knockback seemingly knocks objects towards the projectile rather than away.
To account for these cases, Trigger DWGOs have the option to always induce knockback in the direction of movement.
Similarly, Trigger DWGOs that move so fast that a collision is not even registered should be changed into
raycasting weapons rather than using physical projectiles.

#### Collider DWGOs

Instances of DWGOs that use typical colliders and interact with GameObjects via `MonoBehaviour.OnCollisionEnter()`.
Collider DWGOs are used when the projectile is expected to bounce off of other GameObjects rather than passing through.
As such, these objects _typically_ utilize the physics system to calculate their trajectories.
For example, after a grenade is thrown, it is expected to bounce around the environment using the physics system before exploding.

#### Piercing DWGOs

Instances of Trigger DWGOs that count the number of times they can pierce victims before they are destroyed.
For example, developers may only want a bullet to pierce through 3 enemies before self destructing.

### Weapons

Instances of WGOs that are acitvated by an entity such as a player or enemy (i.e. have `Attack()` and `Cooldown()` methods).

#### DWGO Weapons

Instances of weapons that, once activated, spawn/initialize self regulating DWGOs (i.e. projectiles) that deal damage/healing.
For example, under this system, a gun (DWGO Weapon) that is activated by an entity (player or enemy) would create bullets (self regulating DWGOs) that deal damage.
All variables are stored in the weapon and then injected into the projectile after it has been instantiated.
This way, all parameter tweaking is performed in one place.
As such, all Weapons inherit from the interface corresponding to their assigned DWGO.
For example, Piercing DWGO Weapons inherit from the IPiercingDWGO interface.

## Implementations

Now that the terminology has been explained, let's see how it applies to weapon/obstacle implementations.

### Weaponized GameObject Implementations

The `AWeaponizedGameObject` class is the only infrastructure necessary to implement the most basic of obstacles/traps.
Once able to calculate damage/healing magnitude, Weaponized GameObjects can inflict this magnitude on other GameObjects that they detect through methods such as `OnCollisionEnter()`, `OnTriggerEnter()`, or casting.
These objects inherit from the base infrastructure as shown below.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/wgo-diagram.png" />
</p>

Example implementations of WGOs include spikes, pitfalls, and poison gas clouds.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/spikes-preview.gif" />
    <img src="/assets/images/onion-trail/war-and-peace-system/pitfall-preview.gif" />
</p>

### Basic Weapon Implementations

GameObjects that inherit from `AWeapon` are instances of WGOs that are activated by an outside influence.
Once activated, the basic weapon will deal damage/healing to whatever it interacts with.
These objects inherit from the base infrastructure as shown below.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/basic-weapon-diagram.png" />
</p>

Example implementations of basic weapons include guns utilizing raycasting or melee weapons utilizing overlap spheres to detect other GameObjects.

### Trigger DWGO Weapon Implementations

Trigger DWGOs interact with other GameObjects via the MonoBehaviour.OnTriggerEnter() method.
These objects inherit from the base infrastrucrue as shown below.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/trigger-dwgo-diagram.png" />
</p>

#### Bullet Launcher Weapons

Bullet launchers are an instance of Trigger DWGO Weapons that are further specialized to pierce through a specific number of enemies before self destructing.
Bullets have also been specialized to use raycasting which allows them to elastically reflect off of walls a certain number of times.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/bullet-launcher-1.gif" width=350 />
    <img src="/assets/images/onion-trail/war-and-peace-system/bullet-launcher-2.gif" width=257 />
</p>

#### Melee Weapons

Melee weapons are an instance Trigger DWGO Weapons that are further specialized to pierce through a specific number of enemies before self destructing.
Melee weapons involve swinging a Trigger DWGO radially around the attacker.
Extensions of this base weapon can yield more elaborate swinging animations and projectile skins.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/melee-weapon-preview.gif" />
</p>

### Collider DWGO Weapon Implementations

Collider DWGOs interact with other GameObjects via the MonoBehaviour.OnCollisionEnter() method.
These objects inherit from the base infrastructure as shown below.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/collider-dwgo-diagram.png" />
</p>

#### Grenade Weapons

Grenades are an instance of Collider DWGO Weapons that are further specialized to provide explosive effects upon self destructing.
Extensions of this base weapon can yield more elaborate explosive effects and projectile skins.

<p align="center">
    <img src="/assets/images/onion-trail/war-and-peace-system/grenade.gif" />
</p>

## Knockback Mechanics

Under this system, there are two separate ways to deliver knockback.

- Adding an impulsive force to the target GameObject
- Setting the velocity of the GameObject in the knockback direction for a small period of time.

Adding an impulsive force is fine when knockback is being applied to background GameObjects in the scene such as crates.
However, setting velocity yields much more predictable and standardized results that are independent of external elements such as GameObject mass.
Therefore, setting velocity is intended to be used against entities such as players and enemies.
This functionality is handled by the Entity system.
