---
title: I've just spent 3 days fixing my mistake
date: 2017-11-17 15:04:15
tags:
logoIcon: fa-pencil-square
---

Yes, you've read it right. I made a mistake and it took me 3 days to fix it. Here's what I did and how I fixed it.

note: technical blog post ahead

<!-- more --> 

Yes, you've read it right. I made a mistake and it took me 3 days to fix it. Here's what I did and how I fixed it.

From the beginning of project I knew I will want to support saving and loading. Since this is automation game, it is really important players can save their progress and return to it later. I think there are 2 major ways of saving data to binary file, either automatic or manual. Manual means you have to manually traverse your entire data structure and manually transform every single object into series of bytes you can then write to file stream. This method gives you complete control over bytes you write into file and you can make tons of optimizations because of that. Are ID's of your blocks string? When serializing, you can assign each unique string auto-incremented integer and save integers instead of strings together with lookup table. If your world contains a lot of blocks, this will greatly decrease file size, specially if you use `ushort` instead of `int` (your game won't have more than 65535 different types of blocks, right?) and your string ID's are significantly longer than 2 characters. And that's just one of optimizations you can perform while manually serializing data. But there are of course downsides... One of them is development time because you need to write two methods for every single object you want to serialize and deserialize. It might not seem much but it adds up after a while.

Second approach you can take is automatic binary serialization with C#'s [BinaryFormatter](https://msdn.microsoft.com/en-us/library/system.runtime.serialization.formatters.binary.binaryformatter.aspx) which takes an object and simply serializes it to file stream. If your data is structured as a graph or tree, this is probably the fastest way to save your objects to file and recreate them at later time. There's a caveat though... Classes you want to serialize need to be marked with `[Serializable]` attribute, which means Unity's `Vector3` and `Quaternion` are not serializable by default and since every class in hierarchy need to be marked with `[Serializable]` you can't even extend Unity's classes and make them serializable. Luckily BinaryFormatter provides a way to hook into serialization and deserialization process where you can manually write or read values. In case of `Vector3` that means you have to create serializable version of `Vector3`, coping over values and serializing that serializable `Vector3Serializable`. When deserializing, you just need to convert deserialized `Vector3Serializable` back to `Vector3`.

```csharp
// Serializing Vector3
serializationInfo.AddValue("Position", new Vector3Serializable(Position));
// Deserializing Vector3
Position = (serializationInfo.GetValue("Position", typeof(Vector3Serializable)) as Vector3Serializable).ToVector();
```

Upside of using automatic binary serialization is incredibly easy implementation. From the beginning I've completely split data from presentation, data resides completely in serializable tree and shares it's state via events. Presentation, that is Unity's GameObjects, subscribe to those events and are notified when backing data changes. It's my first game developed this way and it requires a little more boiler-plate upfront but once you have this going, it's very easy to reason about. Your furnace suddenly don't need to know where and how it's inventory is displayed, it simply notifies any potential subscriber that its inventory has changed. Whether the content of inventory is actually displayed or not is irrelevant to furnace and it can go on its merry way of smelting items. Presentation then takes care of conveying that information to the user, be it in form of GUI, in-world floating icon, sound effects or anything else. This way of doing things seems very counter-intuitive and against all Unity tutorials and guides but in practice it pays off really well. One pay-off is easy serialization implementation. 😊

You probably noticed I haven't talked about any mistake yet, right? Well, I had to lay the foundation for further explanation and since you made it this far, here's today's [@duckoftheday](https://twitter.com/duckoftheday).

<blockquote class="twitter-tweet" data-lang="en"><p lang="und" dir="ltr">17 Nov 2017 <a href="https://t.co/fTCWPMfZGu">pic.twitter.com/fTCWPMfZGu</a></p>&mdash; Duck of the day (@duckoftheday) <a href="https://twitter.com/duckoftheday/status/931518865535852545?ref_src=twsrc%5Etfw">November 17, 2017</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Okey, now let's talk about mistake in title. When I was designing objects to represent data and behaviour, I did what was most sensible, I used same class to hold data used by entity and behaviour describing that entity. Data consists of simple private fields and behaviour is contained in methods. Each class also had public events that propagate internal changes in entity's state and are used by presentation to respond to those changes but they are not important in light of this discussion. Using classes to model real world is very much OOP principle and nothing is wrong with it. In fact, I followed [YAGNI principle](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it) refraining to implement things I don't need right now. I managed to implement all the basic mechanics (block placing and breaking) and rendering while having data and behaviour in same class. Only when I came around to actually implementing world saving and loading did I need to refactor a bit of code to separate out data and behaviour. And why did I have to do it? Simply because entity constructor initialized data and and behaviour which was useful when that entity was created for the first time because of player's interaction. However when entity was deserialized, I didn't want to initialize data once again so I had to separate it out and make separate methods for data and behaviour initialization. And it didn't really took me that long, merely a couple of hours so I guess the title was a little click-baity. 😛 Anyway, this refactor helped me find a hidden synchronization bug which I didn't catch beforehand because data and behaviour were so tightly coupled.

While doing al that work, I started thinking whether there are games or prototypes written in Redux. Redux is great paradigm that strongly separates data and behaviour while also introduces immutability of data. Lo and behold, I found [two](https://codepen.io/thepeted/pen/bpovxz) small [games](https://github.com/expo/fluxpybird) and [Unity framework](https://github.com/mattak/Unidux) that use Redux principles... Maybe I'll look into it at my next game jam to see if it's as useful as in web development. Anyway, expect first playable alpha in near future, I've also been working on new UI animations. 😉

<video poster="/2017/11/15/gifs/2017-11-15 18-01-18.png" preload="auto" autoplay="autoplay" muted="muted" loop="loop" webkit-playsinline="">
		<source src="/2017/11/15/gifs/2017-11-15 18-01-18.mp4" type="video/mp4">
</video>