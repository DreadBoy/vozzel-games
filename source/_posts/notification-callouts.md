---
title: Entities can now display notification callouts
date: 2017-11-26 17:09:01
logoIcon: fa-exclamation-triangle
share_cover: /2017/11/26/notification-callouts/2017-11-26 14-39-48.png
---

Last few days I've been working on machine notifications. Imagine your furnace ran out of coal or conveyor belt is backed up... As a game designer, how do you convey this information to the player? 

<video poster="/2017/11/26/notification-callouts/2017-11-26 14-39-48.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/11/26/notification-callouts/2017-11-26 14-39-48.mp4" type="video/mp4">
</video>

<!-- more -->

Last few days I've been working on machine notifications. Imagine your furnace ran out of coal or conveyor belt is backed up... As a game designer, how do you convey this information to the player? 

Ideally each machine would have error state meaning special animation, sound effect and particles for each error state the machine can be in. Is conveyor belt backed up? Drop sparks around the belt and start playing crunchy sounds. Is conveyor belt missing electricity to run? Play mild siren and rubber-band conveyor belt back and forth. But sometimes you simply can't display everything with animations and particle effects and it also never hurts to display same information on multiple screen if it makes sense to do so. Hence I implemented simple notification callout I can display wherever I want. 

It always faces player and if player moves cursor over it, it expands and shows a little bit of text explaining what's wrong. I can now use this callout to notify player that sapling doesn't have enough space to grow but in future I'm going to use them to display all kinds of information, ranging from simple notifications to critical errors.

And here's a gif, showcasing this new callout. 😎

<video poster="/2017/11/26/notification-callouts/2017-11-26 14-39-48.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/11/26/notification-callouts/2017-11-26 14-39-48.mp4" type="video/mp4">
</video>