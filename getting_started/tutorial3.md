# Tutorial 3 - Animation

This page describes how to **animate objects** in the scene and setup **skinned characters**.

Boot up Blender located in Armory SDK and save the blend file. Place a plane object at the grid and change lamp type to **spot**. Create and connect **Sky Texture** to **Background** in world nodes.

![](/getting_started/img/scene3/0.jpg)

Let's start with a cube (that's new!). Add Subdivision Surface and Smooth modifiers to make it look more polished and set color of the material.

![](/getting_started/img/scene3/1.jpg)

We will animate the cube on timeline. Select frame 0 on the timeline and scale cube down to (0.001, 0.001, 0.001). Set Active Keying Set to Scale (alternatively to LocRotScale) and hit **Insert keyframes** (shortcut I). Next, select frame 60, scale cube back up and **Insert keyframes**.

![](/getting_started/img/scene3/2.jpg)

Playing the scene now, we are already able to see cube booming up.

![](/getting_started/img/scene3/3.jpg)

**Duplicate** the cube and select **Clear Animation Data** by right-clicking on the Animation entry of cloned cube in Outliner. This way we can start clean and record new animation.

![](/getting_started/img/scene3/4.jpg)

Set frame to 0 and **Insert keyframes**. Next, set frame to 60, rotate cube 90 degrees on the Z axis and **Insert keyframes**.

![](/getting_started/img/scene3/5.jpg)

By default, Blender will use **Bezier** interpolation mode. However, we want to achieve a constant, linear rotation of the cube. Switch to Graph Editor space, and select **Key - Interpolation Mode - Linear** (shortcut T).

![](/getting_started/img/scene3/6.jpg)

Clone one more cube and clear it's animation data. Select frame 0, move cube forward to Y = 2 and **Insert keyframes**. Select frame 60, move cube back to Y = -2 and **Insert keyframes**.

And that is it! [Play the scene](http://armory3d.org/demo/scene3) to observe animations in real-time.

Get the blend file at [GitHub](https://github.com/armory3d/armory_examples/tree/master/tutorial3).
