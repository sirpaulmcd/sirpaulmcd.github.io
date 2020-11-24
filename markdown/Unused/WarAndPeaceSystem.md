<!-- ---
layout: default
title: WarAndPeace System
permalink: /projects/elite-gardening-squad/warandpeace-system
parent: Elite Gardening Squad
grand_parent: Projects
has_children: false
nav_order: 1
--- -->

# WarAndPeace System
The WarAndPeace System is a generic software architecture for implementing a variety of weapons, obstacles, and items in the Unity game engine.
Since healing is fundamentally the same as dealing damage, it works alongside the Health System to lower **or raise** health points.
The entire system is open source.

## Infrastructure Layout
The classes that make up the WarAndPeace infrastructure can be seen in the image below.

<p align="center">
    <img src="https://cdn.discordapp.com/attachments/779049567844696064/780556837954256926/Base-Infrastructure.PNG" />
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
As such, these objects *typically* neglect the physics system and calculate their own trajectories.
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
As such, these objects *typically* utilize the physics system to calculate their trajectories.
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
    <img src="https://cdn.discordapp.com/attachments/779049567844696064/780556841930588211/Weaponized-GameObjects.PNG" />
</p>

Example implementations of WGOs include spikes, pitfalls, and poison gas clouds. 

<p align="center">
    <img src="https://media.giphy.com/media/o6khUKMV6FOeKzN3Cr/giphy.gif" />
    <img src="https://media.giphy.com/media/1qwsW4kTp1gCQgHpo8/giphy.gif" />
</p>

### Basic Weapon Implementations
GameObjects that inherit from `AWeapon` are instances of WGOs that are activated by an outside influence.
Once activated, the basic weapon will deal damage/healing to whatever it interacts with. 
These objects inherit from the base infrastructure as shown below.

<p align="center">
    <img src="https://cdn.discordapp.com/attachments/779049567844696064/780556838004719646/Basic-Weapon.PNG" />
</p>


Example implementations of basic weapons include guns utilizing raycasting or melee weapons utilizing overlap spheres to detect other GameObjects.

### Trigger DWGO Weapon Implementations
Trigger DWGOs interact with other GameObjects via the MonoBehaviour.OnTriggerEnter() method.
These objects inherit from the base infrastrucrue as shown below.

<p align="center">
    <img src="https://cdn.discordapp.com/attachments/779049567844696064/780556840681472011/Trigger-DWGO-Weapons.PNG" />
</p>

#### Bullet Launcher Weapons
Bullet launchers are an instance Trigger DWGO Weapons that are further specialized to pierce through a specific number of enemies before self destructing. 
Bullets have also been specialized to use raycasting which allows them to elastically reflect off of walls a certain number of times.

<p align="center">
    <img src="https://media.giphy.com/media/GAcX0Q8j8exFNeUiuJ/giphy.gif" width=350 />
    <img src="https://media.giphy.com/media/sTBEs78T6wtxK14LzI/giphy.gif" width=257 />
</p>

#### Melee Weapons
Melee weapons are an instance Trigger DWGO Weapons that are further specialized to pierce through a specific number of enemies before self destructing.
Melee weapons involve swinging a Trigger DWGO radially around the attacker.
Extensions of this base weapon can yield more elaborate swinging animations and projectile skins. 

<p align="center">
    <img src="https://cdn.discordapp.com/attachments/779049567844696064/780571881941630976/Melee-Weapon2.gif" />
</p>

### Collider DWGO Weapon Implementations
Collider DWGOs interact with other GameObjects via the MonoBehaviour.OnCollisionEnter() method.
These objects inherit from the base infrastructure as shown below.

<p align="center">
    <img src="https://cdn.discordapp.com/attachments/779049567844696064/780556839385301022/Collider-DWGO-Weapons.PNG" />
</p>

#### Grenade Weapons
Grenades are an instance of Collider DWGO Weapons that are further specialized to provide explosive effects upon self destructing.
Extensions of this base weapon can yield more elaborate explosive effects and projectile skins.

<p align="center">
    <img src="https://media.giphy.com/media/b4KxdrSaZhBaeRuAHS/giphy.gif" />
</p>

## Knockback Mechanics
Under this system, there are two separate ways to deliver knockback.
- Adding an impulsive force to the target GameObject
- Setting the velocity of the GameObject in the knockback direction for a small period of time.

Adding an impulsive force is fine when knockback is being applied to background GameObjects in the scene such as crates.
However, setting velocity yields much more predictable and standardized results that are independent of external elements such as GameObject mass.
Therefore, setting velocity is intended to be used against entities such as players and enemies.
This functionality is delivered through the `ACombativeEntity` class.
Controllers for entities such as players and enemies are to inherit from this class to participate in systematic knockback.