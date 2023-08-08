---
layout: default
title: Payday Crime War
permalink: /game-development/payday-crime-war
parent: Game Development
# grand_parent: 
has_children: false
nav_order: 1
nav_exclude: false
has_toc: false
---

# PAYDAY: Crime War


<p align="center">
  <a href="https://www.youtube.com/watch?v=pQl-l2Fn25Y">
    <img src="/assets/images/payday-crime-war/payday-crime-war-logo.gif" alt="payday crime way preview" width="600" />
  </a>
  <br />
  <a href="https://www.youtube.com/watch?v=pQl-l2Fn25Y">Payday: Crime War Launch Trailer</a>
</p>

Payday: Crime War is a networked, mobile first-person shooter built using the Unity 3D (C#) game engine where players can compete in PVP game modes or work together to pull off risky criminal PVE heists. Released worldwide and localized into several languages.

I worked as an intermediate gameplay programmer on the project. Although, I was only an intermediate, the development team was relatively small so I was in charge of implementing many core systems/mechanics. Working on a small team meant that I did a little bit of everything. I experienced all stages of development from pre-production to live-ops.

<p align="center">
    <img src="/assets/images/payday-crime-war/payday-crime-war-interaction.gif" alt="payday crime way preview" width="600" />
</p>

My main roles primarily had to do with player controls, player interactions, and the HUD. I implemented player controls bound for use with mobile screens, console controllers, and keyboard/mouse. I created level specific game mechanics/interactions for the various heists. For each mechanic, I introduced responsive visual/audio feedback to ensure a satisfying player experience.

My major contributions include:
- **Interaction:** Heisters could interact with objects in the world to pursue their objective. This included anything from opening doors, placing drills, reviving teammates, picking up items, etc. I implemented the core interaction system and various interactable objects.
- **Inventory:** Inventory systems were required to manage the various item types collected by the heisters. Encumbering objective loot such as cash piles, small bonus loot such as jewelry, and objective items such as keycards were all types of loot that needed to be managed. I implemented the logic to collect, store, and use each loot type.
- **HUD:** The in-game "heads up display" or HUD rendered any visual feedback the player needed to know. This included information such as match progress,  player status, damage/bleed effects, outlines, notifications/alerts, tracking/clamping HUD markers, and related particle effects. I animated HUD elements using a technique called "tweening". Much of my programmer art made it into the final game. 
- **Touch control customization:** Since touch controls take up screen real estate and every player has different preferences, HUD elements had to be fully customizable so players could change the placement, size, and opacity of their touch controls. I made a system that provided this functionality to players with up to 3 custom layouts.
- **Side job progress tracking:** Players were given daily and weekly "side jobs" (i.e. challenges) to encourage them to play the game regularly. I implemented a system to track progress for these challenges in game. I had to make the system modular enough so designers could theoretically make endless challenges. For example, "Get 50 kills with assault rifles as Chains or Wolf in the Cash Grab game mode."
- **Swat phases:** When a mission had gone loud, the amount of swat that could spawn and the times that swat could swarm/retreat were controlled by phases in a hidden system.
- **Notoriety/heat:**: Heisters would gain heat as the mission progressed based on certain actions. The amount of heat determined the difficulty of enemies that could spawn.
- **Auto fire:** Since the game was for mobile, a variety of helpful control options were made available to players. Auto fire was one of these options.

<p align="center">
    <img src="/assets/images/payday-crime-war/payday-crime-war-hud-customization.gif" alt="payday crime way preview" width="600" />
</p>

I created designer facing tools for heist creation. I worked directly with designers to ensure that programmer created tools properly met their needs. I was the mediator between designers and programmers to ensure designers were aware of technical limitations and that programmers had their creative ideas/feedback heard.

I profiled and optimized game performance and memory usage to increase framte rate and reduce thermal throttling for a variety of mobile devices. 

I was also responsible for onboarding/training for new hires and maintaining training resources. This included teaching the use of Git for version control. I mentored junior programmers and provided code reviews to encourage high quality code. I wrote documentation and lead technical talks communicating my gameplay systems and features to the rest of the team.
