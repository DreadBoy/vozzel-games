---
title: Importing Blender models into Unity
date: 2017-11-14 15:48:12
tags:
---

Unity promises to seamlessly import `.fbx` files that were exported from Blender. While that is mostly true, there are still some additional steps we need to take and some caveats we need to be aware off. After fiddling around with Blender and Unity and a lot of help from internet, I managed to compile a list of steps you need to take in order to successfully export model from Blender and use it in Unity and I'm sharing it in following blog post.

<!-- more -->

Unity promises to seamlessly import `.fbx` files that were exported from Blender. While that is mostly true, there are still some additional steps we need to take and some caveats we need to be aware off. After fiddling around with Blender and Unity and a lot of help from internet, I managed to compile a list of steps you need to take in order to successfully export model from Blender and use it in Unity and I'm sharing it in following blog post.

Steps you need to take are roughly:

1. Check model dimensions
2. Export only model meshes
3. Fix scale, rotation and create new prefab

In this post we are going to work on High temperature stone furnace model we created in previous post:

![](HTSF_furnace.png)

## Check model dimensions

This simply means we need make sure our model has sensible dimensions. 1 Blender unit corresponds to 1 meter so you want to make sure your models are not either to big or too small. In my case furnace is 2 meters tall, 1 meter wide and 1 meter deep, centred in lower block. If you need to scale your model, switch to edit mode (`Tab`), select all (`A`) and scale it right down (`S`).

![](HTSF_wireframe.png)

## Export only model meshes

By default Blender will export entire scene to `.fbx`, including lamp and camera. This is undesired behaviour but luckily we can override it with simple toggle button. Select Mesh in export dialogue and export the model. Once you exported, move `.fbx` to Assets directory, switch to Unity and let it import the model.

![](HTSF_export.png)

## Fix rotation and create new prefab

No matter what I tried, imported models were always rotated by -90 degrees on X axis and scaled by 100. I tried changing Blender coordinate space and assigning different world axis to upward and forward axis to no avail. At the end I settled for alternate solution. I create empty GameObject with scale 1 and coordinates (0, 0, 0) and nest model under it. Then I can translate or scale model inside that GameObject until it's perfect. Then I convert that GameObject to prefab and forget I've ever had rough model that was of incorrect rotation and rotation. 😛 Simple and elegant solution, really. Imported furnace next to 1x1x1 cube for scale:

![](HTSF_imported.png)

And there we have it. Together with [previous post](/2017/11/13/Texturing-and-UV-mapping) that is the entire pipeline I've came up with to create and import assets. Keep in mind there's always room for improvement and I might miss something that will even simplify the process. Don't be afraid to experiment!