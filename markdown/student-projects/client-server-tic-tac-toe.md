---
layout: default
title: Client-Server Tic-Tac-Toe
permalink: /student-prjects/client-server-tic-tac-toe/
parent: Student Projects
# grand_parent: Blog
has_children: false
nav_order: 1
nav_exclude: false
has_toc: false
---

# Client-Server-Tic-Tac-Toe
A java based client-server tic-tac-toe application utilizing the MVC design pattern. 
Using these files, you can face your friends over the internet in the ancient art of tic-tac-toe.
The project repo can be found [here](https://github.com/sirpaulmcd/Client-Server-Tic-Tac-Toe).

## How to use
1. Download source code into java project
2. Run `Server.java`
3. Run 2 or more instances of `ClientController.java`

Note that each script can be ran from the same computer to test locally or deployed to a server such that
multiple people can challenge each other over the internet. 

## Preview
Upon launching the client, a player is asked to input their name:
<p align="center">
<img src="/assets/images/client-server-tic-tac-toe/enter-name.png" alt="enter-name.png" width=350 />
</p>

They will then wait to be matched with an opponent. Once found, the game will begin.
The first person to connect to the server is the first person to play.
<p align="center">
<img src="/assets/images/client-server-tic-tac-toe/game-preview.gif" alt="game-preview.gif" width=600 />
</p>


If a person disconnects from the server prematurely, they are shamed accordingly:
<p align="center">
<img src="/assets/images/client-server-tic-tac-toe/rage-quit.png" alt="rage-quit.png" width=400 />
</p>

Useful logs are kept by the server while it is running:
<p align="center">
<img src="/assets/images/client-server-tic-tac-toe/console-logs.png" alt="console-logs.png" width=500 />
</p>

## Learning
This was my first attempt at implementing a client-server architecture. As such, there are things I'd change about the design looking back.
Currently, the client is fat (i.e. contains game logic). 
I did this because I wanted the client to check for the validity of moves before sending them to the server.
However, since tic-tac-toe is such a simple game, I could have serialized the entire game session and passed that along. 
Using a `GameSession.cs` class would have simplified the design because the server would just pass the same self-regulating packet between users.
Instead, I used a `GameState.cs` class that contained information on the game's state and had the client and server update their local game logic accordingly.
It works but it was more complex than necessary. 

