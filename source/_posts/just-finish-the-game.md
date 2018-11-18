---
title: Just finish the damn game!
logoIcon: fa-clock-o
date: 2018-11-18 13:56:12
tags:
---

Hey, another blog post after 10 moths of radio silence! What's happening? 

<!-- more -->

## I finished almost nothing this year

I'm slowly getting bored of starting new projects and putting them on ice halfway through. Admittedly, I finished 2 projects out of 7 I started this year so there's no graveyard of unfinished projects luckily but I still hate how many projects I don't finish. That computer vision project I already have all the hardware I need but can't figure out how to detect what I need in live image? Dead in water. Or that space trading game I thought it'll be really good but it turns out UIs are not that fun? On ice. Or that top down first-person shooter with time rewinding where I figured time rewinding is boring if you want tight game loop? Hanging on nail, collecting dust. That genetic algorithm that calculates optimal starting position for [Dandelifeon](https://ftb.gamepedia.com/Dandelifeon)? Well, I finished that one but it works bad, I can find better starting positions by brute force. It seems that I start many projects but can never bring myself to finish them. 😢

Well, I did finish 2 projects and I finished both of them because they were small and focused. First one was personal cloud that is powered by Raspberry Pi where I can just push a code to some git repo and code gets built and deployed onto Pi. Pi is of course exposed to internet, traffic is encrypted with LetsEncrypt certificate and oncoming traffic is routed to appropriate Node.js app on same Pi. That allows me to very easily deploy public-facing Node.js apps without any additional configuration, all I need is to push to some repo on Pi. Very cool seeing it in action, trust me. 😁 2nd project I finished was Google Home [assistant app](https://assistant.google.com/services/a/uid/000000003a415427) that helps you roll many-sided cube. It's simple but very useful app for D&D players that need to roll lots of cubes. 

> Hey Google, ask Wizard Cuby to roll 10d8 plus 4.  
> *Rolling 10d8 plus 4 for sum of 56!*

## I intend to finish something

Yeah, I said it. I'll finish and publish a game. My goal is to publish to Itch.io and charge some money for it. 5€? Probably but price doesn't matter much, main goal is published game everybody can buy. So let's break down my plan...

1. plan very simple game
2. take out all the features until you are left with even simpler game
3. implement very small set of features that are left after step 2
4. publish the game

After brainstorming for a simple game that is still enjoyable I decided to do infinite space shooter. It should be simple, all you have is a ship, enemies and bullets. No physics, very little game logic, no story and no levels. Not let's cut out even more features from already simple game. Let's drop customisation, you only get 1 space ship. Reduce number of different enemies, 5 is more than enough. We don't need power-ups and special abilities. All we really need is player's HP and score. And infinite number of enemies. Will I be able to implement that? Oh, and we don't need main menu, game over screen with top 5 scores is enough. Let's not complicate things. 💣

Finally I was able to reduce a set of features down to 5:
* player moves ship and shoots bullets
* game spawns new enemies all the time
* enemies move and shoot, behaviour is determined by enemy
* game tracks player's HP and score
* game displays end screen when player is dead

Let's implement this and see how I fare this time...
