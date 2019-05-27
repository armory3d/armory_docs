# Playground Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/H5ylSfTfNg8?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

This tutorial walks you through the Armory basics. We will create a playground-like scene showcasing the essential features step-by-step.

- Get the [.blend file](https://github.com/armory3d/armory_tutorials/releases) for this tutorial.

### Hello World

Pick-up where we left in the [setup tutorial](/getting_started/setup.md). Open Blender, save the project and press `Armory Player - Run` (F5) to play in window.

You can select a runtime in the `Armory Player` panel:
- Select `Krom` to play in stand-alone player.
- Select `Browser` for HTML5 deploy.

You can also select camera mode in the `Armory Player` panel:
- Select `Scene` to start the game from the point of active scene camera.
- Select `Viewport` to start the game from the viewport view. This is useful for quick scene preview as it also lets you control the camera.

Additionally, you can tweak the `Dimensions` in the `Properties - Output` tab for window size. To run in fullscreen, select `Armory Project - Window - Mode - Fullscreen`.

<a href="./getting_started/img/playground/0.jpg">![](/getting_started/img/playground/0.jpg)</a>

### Objects

We will start with some Blender basics on how to manipulate scene objects:

- In 3D View, hit `F3` and type `Add Plane` to create a plane object (or do `Add - Mesh - Plane` from the 3D View header).
- Press `S` to scale up the plane, `R` to rotate, or `G` to grab and translate.
- Delete objects by pressing `X`.

### Modifiers

Blender has a variety of modifiers which apply procedural effects on the active object. Select Cube, navigate to the `Modifiers` tab and add `Bevel` modifier to make the cube edges look polished.

<a href="./getting_started/img/playground/1.jpg">![](/getting_started/img/playground/1.jpg)</a>

### Materials

Select Cube and switch to `Shader Editor`. Enable `Use Nodes`. Now you can tweak the material color and roughness using the default `Principled BSDF` node.

<a href="./getting_started/img/playground/2.jpg">![](/getting_started/img/playground/2.jpg)</a>

Next, switch back to `3D View` and select Plane. We want to put a texture on it. Create a new material in Material tab. Switch to Shader Editor like we did before.

![](/getting_started/img/playground/grid_base.png)
![](/getting_started/img/playground/grid_rough.png)

Save the images above and simply drag-and-drop the files onto the node canvas in Blender. Connect the `Image Texture` nodes to the `Base Color` and `Roughness` sockets of the `Principled BSDF` node.

<a href="./getting_started/img/playground/3.jpg">![](/getting_started/img/playground/3.jpg)</a>

Following these steps, a basic scene is already shaping up. Hit `F5` to play the scene in Armory!

<a href="./getting_started/img/playground/4.jpg">![](/getting_started/img/playground/4.jpg)</a>

### Animation

Let's create an animation rotating the cube. Locate the `Timeline` and go to frame 1. Select Cube and press `I - Rotation` to insert keyframes for the rotation. Next, go to frame 60 in the timeline. With Cube selected, press `R` to rotate it desired amount and press `I - Rotation` again.

<a href="./getting_started/img/playground/5.jpg">![](/getting_started/img/playground/5.jpg)</a>

### Lights

Select light object from hierarchy and switch to `Object Data` tab. You can set the light type and tweak the light color and strength.

<a href="./getting_started/img/playground/6.jpg">![](/getting_started/img/playground/6.jpg)</a>

### Environment

World nodes are used to setup the environment. Switch to `Shader Editor - World` to access the nodes. In this tutorial, we use `Sky Texture` node to render procedural sky. If we were to add an environment map, we would use the `Environment Texture` node coupled with `.hdr` file.

<a href="./getting_started/img/playground/7.jpg">![](/getting_started/img/playground/7.jpg)</a>

### Physics

With object selected, navigate to the `Physics` tab and press the `Rigid Body` button. Set desired shape representing the object in the `Collision` panel.

In the `Rigid Body` panel, set object mass and type:
- Select `Active` for objects which are freely affected by physics.
- Select `Passive` for objects which are static or animated on the timeline.

<a href="./getting_started/img/playground/8.jpg">![](/getting_started/img/playground/8.jpg)</a>

### Asset Import

With Blender, we can easily import common asset formats.
- Select `File - Import` to import file formats.
- Select `File - Append` to import objects from other .blend files.
- Select `File - Link` to link objects from other .blend files.

### Logic Nodes

Logic nodes provide a visual way of creating interactive scenes. When you build your project, created node trees are automatically compiled to scripts.

The system consists of 5 essential categories:
- `Events` - nodes where execution starts, triggered by desired event
- `Actions` - once an event is triggered, these nodes take action
- `Logic` - nodes used to control execution flow, using branching, loops, gates..
- `Variables` - nodes used to store data in a logic tree
- `Values` - nodes used to retrieve data from other objects

We will animate the Cylinder procedurally using logic nodes. Switch to `Logic Editor` area and press `New` to create a new node tree.

You can browse all available nodes through `Add` menu item, or simply hit `Shift + A` to start searching.

- Search for `On Update` node and place it. This is an action node which gets called each frame.
- Connect it to the `Set Location` node.
- Add a `Vector` node and connect it to the `Set Location` node. Each frame, Cylinder location will be set to this vector.
- For the `X` location, add `Math` node and set it to `Sine`.
- Add `Time` node to drive the sine node.
- Add another `Math` node, scaling the sine output.
- We will keep the `Y` and `Z` location unchanged.

Each node tree has to be attached to an object. Select Cylinder and create new `Nodes` trait in `Properties - Object - Armory Traits`. Enter our newly created node tree as `Tree` entry.

<a href="./getting_started/img/playground/9.jpg">![](/getting_started/img/playground/9.jpg)</a>

Note: To see the output of `Print` node, enable `Armory Project - Flags - Debug Console`.

### Haxe Scripts

We can program the object traits directly using the `Haxe` programming language. Let's create a trait which spawns a box after pressing a key.

First, create a cube and name it "Box". Enable `Rigid Body` and `Active` for the cube in the `Physics` tab.

Create an empty object in the scene (`F3 - Add Empty`). The location of this object will serve as the spawning point. Create a new `Haxe` trait in `Properties - Object - Armory Traits`. Press the `New Script` button.

Afterwards, press `Edit Script` to open script file in Kode Studio. Kode Studio is a dedicated code editor which includes code completion and debugging support.

```haxe
package arm;

import iron.object.Object;
import iron.system.Input;
import iron.Scene;
import armory.trait.physics.RigidBody;

class SpawnBox extends iron.Trait {
	public function new() {
		super();
		// We want to get notified every frame
		notifyOnUpdate(update);
	}

	function update() {
		// f key was pressed
		if (Input.getKeyboard().started("f")) {
			// Spawn Box object
			Scene.active.spawnObject("Box", null, boxSpawned);
		}
	}

	// Box just got spawned
	function boxSpawned(o:Object) {
		// Translate cube to the location of empty object
		var traitOwner = object;
		o.transform.loc.setFrom(traitOwner.transform.loc);
		// Box object has a rigid body trait
		// Notify physics system to take new location into effect!
		o.getTrait(RigidBody).syncTransform();
	}
}
```

<a href="./getting_started/img/playground/10.jpg">![](/getting_started/img/playground/10.jpg)</a>

### Bundled Scripts

Armory comes with a set of pre-created bundled scripts. Similar to regular script, bundled script can be attached to an object as a trait. In this tutorial, we will use the `PhysicsDrag` trait. When this trait is attached to physics-enabled object, it lets us drag this object around using the mouse.

### UI Canvas

To build game interface, a dedicated ArmorUI tool is used.

Apart from objects, scene itself can contain traits as well. This is a good fit for UI traits. Switch to `Scene` tab and add a new `UI` trait in the `Armory Traits` panel. Press the `New Canvas` button. Afterwards, `Edit Canvas` button will launch ArmorUI.

In `ArmorUI`, press `Text` button to spawn a text object. Adjust the text in `Properties` panel and hit `Save`. If you launch the game now, canvas will get displayed.

<a href="./getting_started/img/playground/11.jpg">![](/getting_started/img/playground/11.jpg)</a>

### Render Path

Armory is powered by a programmable render path system. Navigate to the `Render - Armory Render Path` panel to access the settings. When creating a new render path, several presets are available for simple configuration.

Multiple render paths can be created. When exporting the project, you can use the render path which best suits the target hardware.

<a href="">![](/getting_started/img/playground/12.jpg)</a>

### Exporter

When we are ready to publish our project, `Properties - Render - Armory Exporter` does the job.

You can create multiple export presets, each specifying a target platform, graphics API, render path and start-up scene. Select desired platform and hit `Publish` button. Once finished, hit `Triangle - Open Folder` to view the exported files.

<a href="">![](/getting_started/img/playground/13.jpg)</a>

- Continue to the [Tanks tutorial](/getting_started/tanks.md)
