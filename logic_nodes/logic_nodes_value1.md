# Values

## Volume Trigger

The lower object-input is used as Volume, the upper one as object-input for the object that enters/leaves/overlaps with it.

Enter-mode: Outputs true on the frame the object enters the volume, on all other frames it outputs false.

Leave-mode: Outputs true on the frame the object leaves the volume, on all other frames it outputs false.

Overlap-mode: Outputs true on the frames the object overlaps with the volume, on all other frames it outputs false.

![](/assets/Volume-trigger.JPG)


## Active Camera

Outputs the current active Camera in your game as object.

![](/assets/active-camera.JPG)

## Active Scene

Outputs the currently active scene in your game.

![](/assets/active-scene.JPG)

## Get Transform

Outputs the current transform of the set object. An objects Transform consists out of Vectors for its global location, rotation, and scale.

![](/assets/get-transform.JPG)


## Get Location

Outputs the current global location of the set object as vector.

![](/assets/get-location.JPG)


## Get Rotation

Outputs the current rotation of the set Object as a Vector.

![](/assets/get-rotation.JPG)


## Get Scale

Outputs the current scale of the set object as vector.

![](/assets/get-scale.JPG)


## Get Object

Searches for an object with the set name in the scene and outputs it.

![](/assets/get-object.JPG)


## Get Visible

Outputs a Boolean Value according to the objects current visibility setting in the Outliner. False if invisible, True if visible, even if the Object is not on camera right now.

![](/assets/get-visible.JPG)


## Get Child

Searches for object with the set name that is currently a child of the set object and outputs it.

![](/assets/get-child.JPG)


## Get Children

Outputs all current children of the set object as array of objects.

![](/assets/get-children.JPG)


## Get Parent

Outputs the current closest parent of the set object.

![](/assets/get-parent.JPG)


## Get Group

Searches for a group of objects with the set name and outputs it as an array of objects.

![](/assets/get-group.JPG)


## Group

Outputs all objects in the set group as array.

![](/assets/group.JPG) 


## Get Distance

Outputs the current distance between the two set objects as float.

![](/assets/get-distance.JPG)


## Get Trait

Searches for a Trait with the set name which is applied on the set object and outputs it.

![](/assets/get-trait.JPG)


## Get Property

Can be used to receive Properties of other objects, which were set with the "[Set Property](/logic-nodes/set-property.md)" node. The properties name and object have to match the inputs of this node.

![](/assets/Get-property.JPG)