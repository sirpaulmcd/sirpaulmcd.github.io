---
layout: default
title: WarAndPeace System
permalink: /projects/elite-gardening-squad/warandpeace-system
parent: Elite Gardening Squad
grand_parent: Projects
has_children: false
nav_order: 1
---

# WarAndPeace System
The WarAndPeace System is a generic software infrastructure for implementing a variety of weapons/traps in the Unity game engine.
Since healing is fundamentally the same to dealing damage, it works alongside the Health System to lower **or raise** health points.
That is why it is called the WarAndPeace System. 

## Infrastructure Summary
The following is a high level summary of the system infrastructure necessary to implement a variety base weapons.
The classes that make up the WarAndPeace infrastructure can be seen in the image below.

*PICTURE*

### Weaponized GameObjects (WGOs)
Any GameObject that is expected to deal damage/healing (i.e utilizes the IWarAndPeace interface).
A fundamental attack systems calculate damage/healing magnitude based on several parameters.
The magnitude can be anywhere between the minimum/maximum damage values.
A critical chance determines whether this magnitude will be multiplied by the critical multiplier.
In addition to damaging/healing, a weaponized GameObject can also apply knockback effects from the specified origin.
A desirable knockback origin changes depending on the implementation.
For example, the knockback origin of a bullet should be the bullet itself whereas the knockback origin of a melee weapon should be the attacker.

### Dynamic Weaponized GameObjects (DWGOs)
Instances of WGOs that are dynamically spawned, move through space, and interact with GameObjects that touch their colliders.
DWGOs are self regulating projectiles. 
After being spawned into a scene and initialized by their corresponding weapon, they are responsible for themselves.
and self destruct after a designated amount of time unless otherwise specified. 
It is important to note that all DWGOs (i.e. projectiles) should be placed on the "Ignore Raycast" layer to avoid complications. 

#### Trigger DWGOs
Instances of DWGOs that use trigger colliders and interact with GameObjects via MonoBehaviour.OnTriggerEnter().
Trigger DWGOs are used when the DWGO is expected to pass through other GameObjects.
As such, these objects *typically* neglect the physics system and calculate their own trajectories.
For example, a bullet may be expected to pass through multiple enemies without bouncing off and changing direction.
Same could be said for a melee weapon.
In some cases, you may want a Trigger DWGO that travels through some objects but reflects off of others.
For instance, a bullet that travels through enemies but ricochets off of walls.
In these situations, ricocheting can be simulated using methods such as Raycasting (see bullet implementation).
Additionally, fast moving TriggerDWGOs can surpass the transform of their targets before a collision is registered.
As a result, the induced knockback seemingly knocks objects towards the projectile rather than away.
To account for these cases, Trigger DWGOs have the option to always induce knockback in the direction of movement.
Similarly, Trigger DWGOs that move so fast that a collision is not even registered should be 

#### Collider DWGOs
Instances of DWGOs that use typical colliders and interact with GameObjects via MonoBehaviour.OnCollisionEnter().
Collider DWGOs are used when the DWGO is expected to bounce off of other GameObjects rather than passing through.
As such, these objects *typically* utilize the physics system to calculate their trajectories.
For example, after a grenade is thrown, it is expected to bounce around the environment using the physics system before exploding.

#### Piercing DWGOs
Instances of Trigger DWGOs that count the number of times they can pierce victims before they are destroyed. 
For example, developers may only want a bullet to pierce through 3 enemies before self destructing.

### Weapons
Instances of WGOs that are acitvated by an entity such as a player or enemy (i.e. have an Attack() method).

#### DWGO Weapons
Instances of weapons that, once acitvated, spawn/initialize self regulating DWGOs that deal damage/healingl.
For example, under this system, a gun (DWGO Weapon) that is activated by an entity (player or enemy) would create bullets (self regulating DWGOs) that deal damage.
For ease of use, all variables are stored in the weapon and then injected into the projectile after it has been instantiated.
This way, all parameter tweaking takes place on the weapon GameObject and the resulting projectiles reflect these parameters.
As such, all Weapons inherit from the interface corresponding to their assigned DWGO.
For example, Piercing DWGO Weapons inherit from the IPiercingDWGO interface.

## Implementations
Now that the fundamental system infrastructure has been explained, let's see how it applies to weapon/trap implementations.

### Weaponized GameObject Implementations
The AWeaponizedGameObject class is the only infrastructure necessary to implement the most basic of obstacles/traps.
By inheriting from this abstract class, GameObjects that use OnCollisionEnter, OnTriggerEnter, or casting can deal damage/healing.
These objects inherit from the base infrastructure as shown below.

*PICTURE*

Example implementations of WGOs include spikes, pitfalls, and poison gas clouds. 

*PICTURE*

### Basic Weapon Implementations
GameObjects that inherit from AWeapon are instances of WGOs that are activated by an outside influence.
By inheriting this abstract class, once activated, the weapon will deal damage to whatever it interacts with. 
These objects inherit from the base infrastructure as shown below.

*PICTURE*

Example implementations of Weapons include guns utlizing raycasting or melee weapons utilizing overlap spheres to detect other GameObjects.

### Trigger DWGO Weapon Implementations
Trigger DWGOs interact with other GameObjects via the MonoBehaviour.OnTriggerEnter() method.
These objects inherit from the base infrastrucrue as shown below.

*PICTURE*

#### Bullet Launcher Weapons
Bullet launchers are an instance Trigger DWGO Weapons that are further specialized to pierce through a specific number of enemies before self destructing. 
In addition to piercing capabilities, bullets have also been specialized to use raycasting to elastically reflect off of walls.
As such, bullets self destruct after either running down the piercing count or the ricochet count. 

*PICTURE*

#### Melee Weapons
Melee weapons are an instance Trigger DWGO Weapons that are further specialized to pierce through a specific number of enemies before self destructing.
Melee weapons involve swinging a Trigger DWGO radially around the attacker.
Futher specializations of this weapon can yield more complex swinging animations and projectile skins. 

*PICTURE*

### Collider DWGO Weapon Implementations
Collider DWGOs interact with other GameObjects via the MonoBehaviour.OnCollisionEnter() method.
These objects inherit from the base infrastructure as shown below.

*PICTURE*

#### Grenade Weapons
Grenades are an instance of Collider DWGO Weapons that are further specialized to provide explosive effects upon self destructing.
Fuether specializations of this weapon can yield different explosive effects and projectile skins.

*PICTURE*

## Knockback Mechanics
Under this system, there are two separate ways to deliver knockback.
- Adding an impulsive force to the target GameObject
- Setting the velocity of the GameObject in the knockback direction for a small period of time.

Adding an impulsive force is fine when knockback is being applied to background GameObjects in the scene such as crates.
However, setting velocity yields much more predictable and standardized results that are independent of external elements such as GameObject mass.
Therefore, setting velocity is intended to be used against entities such as players and enemies.
This functionality is delivered through the ACombativeEntity class.
Controllers for entities such as players and enemies are to inherit from this class to participate in systematic knockback.

*PICTURE*