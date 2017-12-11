# Traits

Armory uses a trait(component) system to insert logic into Blender objects and make them interactive. Traits can be attached to scene objects or scenes itself. To inspect traits placed in the scene, switch to `Groups` view in the `Outliner`.

There are several trait types:
- `Haxe Script` - writing script from scratch in Haxe
- `Bundled Script` - handling common stuff like character controllers, bundled in Armory
- `Logic Nodes` - assembling logic visually
- `Canvas` - working with user interface

For scripts, it is possible to pass parameters or set script properties straight from Blender.

## Trait events

Trait exposes events - this makes it possible to get notified about its life-cycle.

- `Trait.notifyOnAdd()` - trait is added to an object
- `Trait.notifyOnInit()` - object which this trait belongs to is added to scene
- `Trait.notifyOnRemove()` - object which this trait belongs to is removed from scene
- `Trait.notifyOnUpdate()` - update game logic here
- `Trait.notifyOnRender()` - update rendering here

As the scene is being built asynchronously, `onInit` event can get called at a time when not all scene objects are present yet. If trait construction depends on other scene objects, it is possible to use `Scene.active.notifyOnInit()` event which gets called as soon as the scene is fully constructed.
