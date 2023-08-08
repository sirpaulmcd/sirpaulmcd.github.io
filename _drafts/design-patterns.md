---
layout: default
title: Design Patterns
permalink: /tutorials/design-patterns/
parent: Tutorials and Cheat Sheets
# grand_parent: Blog
has_children: true
nav_order: 2
nav_exclude: false
has_toc: false
---

# Design Patterns

Design patterns are generalized, reusable solutions to common software problems. If you are a software developer, you face new problems on a regular basis. Why reinvent the wheel when you can apply universally recognized design patterns in half the time? These patterns are the culmination of generations of software expertise and have stood the test of time due to their practicality. However, that doesn't mean they are the best solution to every problem. After all, they are generalizations and you shouldn't just jump into using a design pattern without thinking about potentially better solutions. It also doesn't mean they are perfect. There are almost certainly better design patterns waiting to be discovered. Regardless of these flaws, being familiar with the fundamental design patterns will make you a better developer and give you a proper foundation to begin making your own, optimized design patterns as you gain more expereince.

Software patterns were first conceptualized in 1977 in the book [A Pattern Language](https://en.wikipedia.org/wiki/A_Pattern_Language). However, more infamously in 1990, a group called the Gang of Four (GoF) released [Design Patterns: Elements of Reusable Object-Oriented Software](https://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612) which documented 23 universal design patterns and is widely considered to be "the bible" of object-oriented design patterns. This may be the case for people who have a good knowledge of C++ and don't mind burning through an entire textbook in their free time. However, if you're like me, the Java oriented [Head First Design Patterns](https://www.amazon.com/Head-First-Design-Patterns-Brain-Friendly/dp/0596007124) is a much more approachable resource for learning design patterns. 

There are 3 major types of design patterns:

- [**Creational Patterns**]()
  - Design patterns that decouples scripts from the objects that it needs to instantiate. Essentially, these patterns offload the responsibility of object instantiation. This way, objects can be created without the additional complexity/dependency involved with calling the constructor directly.
- [**Structural Pattenrs**]()
  - Design patterns that use inheritance to assemble objects into larger structures with additional functionality. 
- [**Behavioural Patterns**]()
  - Design patterns that regulate the interations and destribute responsibility between objects. 
