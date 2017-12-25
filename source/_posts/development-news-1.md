---
title: Development news on 11. December 2017
date: 2017-12-11 16:32:47
logoIcon: fa-newspaper-o
share_cover: /2017/12/11/development-news-1/2017-12-04 11-06-24.png
---

In first edition of Development news we are going to take a look at progress so far, rant about Twitter's crappy video compression and make predictions about first public alpha.

<!-- more -->

In first edition of Development news we are going to take a look at progress so far, rant about Twitter's crappy video compression and make predictions about first public alpha.

## Twitter compresses video to oblivion and I don't like it

I like to frequently show off progress on Twitter in form of short videos because they are so easy to record but I noticed those videos look much worse on Twitter than on my computer. At first I thought it's because I viewed them on 4G but even when I switched to fast Wi-Fi quality didn't improve. And as far as I can tell, this won't change in the near future. I also tried Imgur and Gfycat but their Twitter integration is non-existent hence I'm not going to use them. So, until I figure out how to easily and quickly transcode video to gif I'm forced to spread those low quality videos. But fear not, I can still upload full resolution videos to my blog and display them in their full glory right here. 😁

## Recent changes and additions

Did I mention I love Git? Currently I'm using it to manage the project and by using `git log --since="2017-11-11"` I can display all commits I made since I started writing this blog, that date being 11. November 2017. It says I made 115 commits, changing (added or removed) 23483 lines of code in 360 files. 😲 Luckily I can also display all commit messages since that date and in case you want to comb through my Git history, you are welcome to do so. Reading back, some commit messages really don't make sense... 

<details><summary>Click to see all commit messages</summary><samp>Collect Player and Skyworld under one parent to make saving to file easier
Create serializable version of Vector3 and Quaternion
Allow keys to be unsubscribed
Change serialization to vanilla C# BinaryFormatter
Remove unused manual serialization methods
Correctly rotate all entity prefabs
Fix compilation warnings
Release some more resources when clearing server data
Start working on Main Menu
Add custom Skyboxes to main menu and game
Add Nova Mono and Open Sans fonts
Create button element
Create text element
Make inventory slot background sliced
Create WorldList animations
Fix strange problem with button controller
Move saves directory to MyDocuments
List world entries in main menu
Load world from world list
Split data and behaviour of entities
Save and load player's rotation
Copy server inventory to client inventory to break reference. Otherwise changes to client inventory effected server inventory.
Improve code for clicking the slot
Rename some filenames of classes
Split entity Initialize method into 2 methods, one for behaviour and one for data
Fix yet another bug with null Parent in InventorySlot
Make entity UIs static size
Don't override UnityEngine.Object.name
Release cursor when going to main menu
Don't destroy Main Menu UI immediately because EventSystem freaks out
Start working on actual implementation of HTSF
Consolidate all block and item textures
Respect block rotation when rendering faces of block
Implement sticky blocks and correct block rotation
Implement transparent blocks
Request selected slot when start rendering inventory bar
Move materials to correct directory
Repack tiles spritesheet with TexturePacker
Improve backdrop of EntityUI
Nest all block colliders under one object
Rotate wood texture to be horizontal
Move generic canvas element to Elements directory
Add dirt, grass and oak sapling
Remove entity data when removing entity
Update TODO
Add OakSapling entity
Run entity's CanPlace method when placing entity
Check space before growing tree
Make leaves non-transparent
Create simple FPS counter
Start working on callout
Use callout with oak sapling
Check in some random Unity settings
Reduce size of cursor
Remove callout when breaking sapling
Change ItemType from readonly to const
Implement axe behaviour
Destroy only those log blocks that were created by tree
Wire up events for dropped items and use simple renderer
Defer moving of dropped item to ItemRenderer
Use Unity physics to detect collision
Improve position interpolation for dropped items
Nest items under world renderer (to ensure destruction)
Calculate distance item moved in last frame to improve rendering
Code cleanup
Change gradient of slope that allows item sliding
Drop item only if you actually have it
Move rendering of dropped items into ItemRenderer
Add LogFormat methods for warning and error
Add rendering for entities
Implement renderer for items that don't have block form
Create windmill model
Animate rotation and export it to Unity
Update Windmill animations and add icon
Remove unsused assets
Add blend1 files to .gitingore
Add NoUI flag to BaseEntity
Add code necessary for windmill
Implement child multiblocks for windmill
Create BetterAnimator component that prevents visits to same state
Add some helper classes
Calculate strength of windmill and update animation
Finally fix incorrect vertex order. You should start from bottom left from beginning!
Render only blocks that were updated
Unsubscribe from events
Improve animation for Windmill
Move .psd to correct directory
Add shaft entity
Implement rotation for shaft
Apparently 'new' keyword doesn't complain if base method is incompatible.
Use drop mechanic in Axe tool
Rework inventory background
Create prefab for tooltip
Use actual text in tooltip
Improve tooltip scaling
Create tooltip data for all items
Transmit transmission through shaft
Change shaft model
Reduce border on tooltip
Hide shortcuts behind compile flags
Stop transmiting power when entity is destroyed
Add Transmission Splitter
Hide or show tooltips when taking or placing items in inventory
Add bevel gear for transmissions
Rework model of transmission splitter
Rotate sticky blocks depending on player's location
Separately control speed of splitter parts
Create new icon for mechanical splitter
Satisfy compiler warnings
What if I bump up quality?
Allow game to run in background
Tie player movement to physics updates instead of render updates
Don't divide power in splitter, just transmit the same on both sides
Make player movement speed nondependent on framerate
</samp></details>


To sum up changes in last month: saving and loading, main menu, first machines and tools, QOL improvements (tooltips, callouts). I also optimized world rendering but unless you are really observant, you won't notice any changes. Question at that point is probably *"When are you going to release something we can play?"*. And the good news is I expect to release first public alpha in a couple of weeks. Goal for first release is full implementation of first process that will take you from basic automatic tree farm all the way to windmill crafting. Hopefully this will give us first feeling of what the gameplay will look like. But to achieve that, I need to expand functionality of tools since they can currently be used only by player and also add a bunch of machines for different operations in mention process.

## Reposted videos

And here are all videos and pictures I posted to Twitter but I'm reposting here in full quality. Enjoy!


<video poster="/2017/12/11/development-news-1/2017-12-01 20-27-23.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/11/development-news-1/2017-12-01 20-27-23.mp4" type="video/mp4">
</video>


<video poster="/2017/12/11/development-news-1/2017-12-02 10-28-07.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/11/development-news-1/2017-12-02 10-28-07.mp4" type="video/mp4">
</video>


<video poster="/2017/12/11/development-news-1/2017-12-04 11-06-24.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/11/development-news-1/2017-12-04 11-06-24.mp4" type="video/mp4">
</video>


<video poster="/2017/12/11/development-news-1/2017-12-06 16-04-50.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/11/development-news-1/2017-12-06 16-04-50.mp4" type="video/mp4">
</video>


<video poster="/2017/12/11/development-news-1/2017-12-07 18-39-34.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/11/development-news-1/2017-12-07 18-39-34.mp4" type="video/mp4">
</video>


<video poster="/2017/12/11/development-news-1/2017-12-10 12-46-37.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/11/development-news-1/2017-12-10 12-46-37.mp4" type="video/mp4">
</video>


<video poster="/2017/12/11/development-news-1/2017-12-11 11-35-19.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/11/development-news-1/2017-12-11 11-35-19.mp4" type="video/mp4">
</video>

![](Colour space in Unity.png)