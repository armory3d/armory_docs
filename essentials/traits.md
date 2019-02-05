# Traits

Armory uses a trait(component) system to insert logic into Blender objects and make them interactive. Traits can be attached to scene objects or scenes itself. To inspect traits placed in the scene, switch to `Orphan Data` view in the `Outliner` and see Collections.

![](/essentials/img/traits_groups.png)

There are several trait types:
- `Haxe` - writing script from scratch in Haxe
- `Bundled` - handling common stuff like character controllers, bundled in Armory
- `Nodes` - assembling logic visually
- `UI` - working with canvas & user interface

For scripts, it is possible to pass parameters or set script properties straight from Blender.

![](/essentials/img/traits_panel.png)

## Trait events

Trait exposes events - this makes it possible to get notified about its life-cycle.

- `Trait.notifyOnAdd()` - trait is added to an object
- `Trait.notifyOnInit()` - object which this trait belongs to is added to scene
- `Trait.notifyOnRemove()` - object which this trait belongs to is removed from scene
- `Trait.notifyOnUpdate()` - update game logic here
- `Trait.notifyOnRender()` - update rendering here

As the scene is being built asynchronously, `onInit` event can get called at a time when not all scene objects are present yet. If trait construction depends on other scene objects, use `Scene.active.notifyOnInit()` event which gets called as soon as the scene is fully constructed.

## Trait folder organisation

By default all traits are created into your project's "Sources/arm" folder when you create them in Blender.

![](/essentials/img/subfolders/1-Regular_Trait.png)
![](/essentials/img/subfolders/2-Regular_Trait_Source.png)

In general it's desirable to create a folder structure that matches logically your game division. For example you could decide to split your game in multiple scenes, and ideally keep the code of each Scene in separate subfolders (one per scene) so that it's easy to maintain later on.

In order to create a folder hierarchy tree in armory, you can use the `Haxe package syntax` when assigning a name to your new trait. Therefore if you assign a name such as `general.BoxBehavior`, a new trait will be created under "Sources/arm/general" subfolder, with name "BoxBehavior.hx".

![](/essentials/img/subfolders/3-Subfolder_Trait.png)
![](/essentials/img/subfolders/4-Subfolder_Trait_List.png)
![](/essentials/img/subfolders/5-Subfolder_Trait_Source.png)

You can create infinitely nested subfolders this way by appending more dot-separated names to the trait name, such as "general.terrain.TerrainCollider" which will create a file named "TerrainCollider.hx" under the path "Sources/arm/general/terrain".

If at some point you want to assign a different trait to your object, you simply need to select the trait from the list displayed when you click on the `Class` dropdown, right below the Traits List.

![](/essentials/img/subfolders/6-Trait_List.png)
![](/essentials/img/subfolders/7-Subfolder_Trait_Assigned.png)

Note: Please bear in mind that some reserved words won't be allowed to be used as package names, therefore trait names such as "my.new.Trait" won't be valid due to `new` being a reserved word.
