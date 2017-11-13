---
title: Texturing and UV mapping
date: 2017-11-13 17:06:11
tags:
---

I'm a great fan of retro pixe land lowpoly art styles and for my latest game project I'm trying my hands at recreating it. My biggest inspirations so far are Terraria, Minecraft and to an extend Stoneheart and I'm trying to recreate those styles. I have almost zero artistic skills so for the starter I decided to use free textures created by Kenney and combine them to create complete textures for machines. After following [Blender's tutorial](https://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/UV_Map_Basics) I was familiar with how to unwrap cube and apply texture to it but this where the tutorial ended. When I tried texturing more complex objects I failed spectacularly and after finally figuring it out, I decided to write simple step by step advice on how I did it. I'm going to walk you through texturing new machine, High temperature stone furnace. This is how it's going to look like at the end: 

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Got first multiblock structure into the game and also implemented some basic automation. Things are shaping up :) <a href="https://t.co/SNFxKxKBYY">pic.twitter.com/SNFxKxKBYY</a></p>&mdash; Matic Leva (@Dread_Boy) <a href="https://twitter.com/Dread_Boy/status/929976795851616256?ref_src=twsrc%5Etfw">November 13, 2017</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<!-- more --> 
You should first read the tutorial I mentioned and then come back for additional tips.

## Mark seams and unwrap carefully
This is where I failed first. Blender tutorial shows you how to mark seam and then how to unwrap the object but I either didn't read carefully enough or didn't understand implications. Seams are where texture is going to split and not every edge should be marked as seam. I found the easiest way to mark correct seams and it is by imagining the object as if it is made out of paper and you are trying to unfold it. Something [like this](https://www.wikihow.com/Make-a-3D-Cube). Once I realised this, it became very simple to unwrap semi-complex model of high temperature stone furnace. Seams are marked as red in picture below:

![](HTSF_seams.png)

If you now select all faces of model and unwrap it, you will get this nice shape you can print out and create your own furnace out of paper. 😉 But sadly, UV map is still turned sideways and it's going to be pain to create texture like that in Photoshop.  

![](HTSF_unwrap_first.png)

Neat trick to precisely rotate it is to place cursor at center of image and rotate UV map around this cursor. To center cursor precisely, open panel by pressing `N` and enter cursor location, mine was (256, 256) but number depend on your texture size. Then change rotation pivot to 2D cursor:

![](HTSF_cursor.png)

Now we can finally rotate UV map by using `R`, typing `90` and pressing `Enter`. I love how Blender is all about keybinds, I wish more apps and website supported navigation with keyboard.

## Create texture with your favourite image editor
Now that we created UV map, we can finally apply our texture to it. Or we could if we had it... After unwraping and tyding up the UV map, you should export UV map to simple `.png` by going to `UVS -> Export UV Layout` and then edit that .png in paint.net or Photoshop. For this texture I used Photoshop but Crate's and Furnace's textures were created in paint.net. 🙂 Anyhow, now that you've got the texture, simply follow the rest of Blender's tutorial and you should be good to go. This is how finished furnace looks like in Blender:

![](HTSF_finished.png)

Sadly, at that point your journey is not finished yet since you still need to export the model, import it into Unity, avoid common mistakes and fix incorrect scales. All of this is really topic for itself so I'm going to talk about it in next blog post. Have a great day!