---
title: Development news on 22. December 2017
date: 2017-12-22 19:43:55
logoIcon: fa-newspaper-o
share_cover: /2017/12/22/development-news-2/thumbnail.png
---

Christmas is here and with that also 3 new machines. 🙂 In a light of upcoming public alpha I worked on implementing machines needed for first automated tree farm and reworked world renderer again. 

![](/2017/12/22/development-news-2/thumbnail.png)

<!-- more -->


Christmas is here and with that also 3 new machines. 🙂 In a light of upcoming public alpha I worked on implementing machines needed for first automated tree farm and reworked world renderer again. 

## Better way of rendering blocks

First thing I tackled was world renderer. Improvements allowed me to create breaking and placing animations for a block and will allow me to iterate some more on that front. Right now a block that you break will simply scale down and fall away from you before disappearing completely but in the future I can add particle effects, slice up block in many piece and make those fall apart, possibilities are endless. And how did I achieve that? Simple, really. Before I used to re-render world mesh each time something changed. Did you break a block? Better throw away old mesh, generate new one for entire world and replace it. For uninitiated, mesh is a collection of vertices, triangles and texture data that makes up all 3 models. In Unity you can generate new mesh on fly and since my world uses discrete blocks, this generation is pretty easy, they are just cubes. Of course I don't generate cube face that are not visible to player and I have to take into account block rotation but ultimately they are just simple cubes, easy to reason about. 

But this approach has a flaw. I have to re-render the world each time a block is changed simply because I have nothing that connects blocks in data to vertices in mesh. If player destroys a block, I have no way of tracing that to a set of vertices and triangles and splicing them out of mesh. You can see why this might not be the best implementation... So, I changed things up a bit and decided to cache mesh data separately for each block before joining them together. This allows for less calculations since I only need to recalculate a mesh of 7 blocks every time a block is destroyed; I need to check the block that was updated and all neighbouring 6 blocks. You can probably see where optimizations was done. 😉

<figure><video poster="/2017/12/22/development-news-2/2017-12-15 13-27-30.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/22/development-news-2/2017-12-15 13-27-30.mp4" type="video/mp4">
</video><figcaption>Breaking and placing animations</figcaption></figure>

## New machines and first semi-automation

I've been also hard at work to implement first machines. So far you can chop down trees, blow items across the plane, transport them with conveyor belts and store them in chests.

### Tree chopper

Tree chopper is a simple machine that requires mechanical power and an axe and will chop down tree in front of it. First connect it to windmill, then give it an axe (just right click machine while holding axe in hand) and this little machine will do the rest. You will know everything was done correctly if you see an axe swinging in front of machine. 

<figure><video poster="/2017/12/22/development-news-2/2017-12-16 12-16-11.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/22/development-news-2/2017-12-16 12-16-11.mp4" type="video/mp4">
</video><figcaption>Tree choppers in action</figcaption></figure>

### Mechanical fans and conveyor belts

These 2 machines are your early game means of item transportation. Mechanical fan requires power and will blow items in 3x3 area 7 blocks away. If you place it above tree chopper, it will provide easy way of collecting items that are dropped when trees is felled by tree chopper.  

<figure><video poster="/2017/12/22/development-news-2/2017-12-17 17-00-53.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/22/development-news-2/2017-12-17 17-00-53.mp4" type="video/mp4">
</video><figcaption>Small and simple tree farm. Man, this shafts are way too complicated, I have to rethink that...</figcaption></figure>

Item collected at one place can then be picked up by conveyor belt, transported to your storage area and then inserted into chest.

<figure><video poster="/2017/12/22/development-news-2/2017-12-25 12-21-25.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/12/22/development-news-2/2017-12-25 12-21-25.mp4" type="video/mp4">
</video><figcaption>This ain't storage area but you get the idea. 😃</figcaption></figure>

<hr>

Don't forget to follow me in [Twitter](https://twitter.com/Dread_Boy) for regular development updates and subscribe to [RSS feed](http://vozzel.games/atom.xml) if you still use that kind of thing.