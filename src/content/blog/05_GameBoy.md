---
title: 'Game Engine'
description: 'Raspberry Pi Pico Game Engine'
pubDate: 'Mar 21 2026'
heroImage: '/public/assets/05_GameEngine/00_Logo.png'
---

<!-- summary -->
This is my big passion project. During the arcade course we had a temporary idea of adding fans to simulate the wind for the player which led to me buying my own **Raspberry Pi Pico** microcontroller sample kit. After some smaller projects and lots of tutorials I wanted to use my game design education to combine with my new found passion. And after I played Pokemon on my old GameBoy color I had the right inspiration on what that new project should be. I want to create my own handheld consol to be able to create and play my own games on it. For this project I used _Visual Studio Code_ with _C++_ and the _Raspberry Pi Add On_.

In addition with a guest lecture we had about **Entity-Component-Systems**, which I found a very interesting concept but never had the chance to implement it, I had the architectual structure for this project set and only needed to start. From struggles with getting my Physics engine to run and also implementing a file system onto my SD card reader to unlock spritesheets and animations for my projects I have a prototype working now. 

The next steps are to create my own games for it. I still have the dream of creating my own small version of Pokemon as well as some other Mini games.

//TODO: add pictues of the physical object
//TODO: add clips of games

<!-- links -->
Take a look at  <a href="https://github.com/JulianLet/ShadertoyClone" target="_blank" rel="noopener noreferrer">GitHub</a>


This is my big passion project: a **handheld game console** built using a Raspberry Pi Pico microcontroller. Inspired by playing Pokemon on my old GameBoy Color, I wanted to create a device that could run my own games. I use _Visual Studio Code_ with _C++_ and the _Raspberry Pi Add-On_ to develop games and the underlying engine.

After learning about **Entity-Component-Systems** in a guest lecture, I structured my engine around this architecture. The prototype already supports a physics engine, sprite sheets, animations, and a file system on the SD card.

This project has taught me a lot about combining hardware and software in a game development context. From implementing an Entity-Component-System, building a physics engine, to managing sprite sheets and file systems on an SD card, I have learned how to structure a large-scale, modular game engine. Seeing my own games run on a custom handheld device is incredibly rewarding, and I look forward to continuing development and creating full games on it.

In this project, I’m working within the strict hardware limits of the Raspberry Pi Pico, which has very limited RAM and flash memory. This forced me to carefully manage assets, memory, and CPU usage to ensure the engine could run smoothly. I designed a compact, efficient architecture that handles physics, input, rendering, and file management for spritesheets and animations, all while keeping resource usage minimal. The current prototype showcases several small games, including a Pong clone, a Jump'n'Run demo, and a tilemap/animation demo where the player can walk around a small area. Balancing functionality with strict memory and performance constraints has been one of the most rewarding and technically challenging aspects of this project.