# Reference

## Logic

### Alternate

Alternates between its activated outputs to pass through its input when it is being re-activated.  

![](/logic_nodes/img/Alternate.JPG)


### Array loop

It loops through each item assigned in an array."Value" give item specified by index's value."Done" calls connectors when it is done looping through the array.

![](/logic_nodes/img/array-loop.JPG)


### Branch

When activated, activates its "True" or "False" output, according to the state of the plugged-in boolean.

![](/logic_nodes/img/Branch.JPG)


### Gate

Logic nodes way to do "if" statements. When activated, it compares if its two inputs are being Equal, Greater Equal, Less Equal, or Not Equal, regardless of variable type, and passes through its red input if the set state is the case.

"And" and "Or" are being used for booleans only, and pass through the input when both bools are true \(and\) or at least one \(or\).

![](/logic_nodes/img/Gate.JPG)


### Inverse

Bool will become opposite, True will become False, False will become True.

![](/logic_nodes/img/Inverse.JPG)


### Is True/False

Passes through its activation only if the plugged in boolean is "True"/"False", according to the node.

![](/logic_nodes/img/Is-true_false.JPG)


### Is None

Give bool value of null i.e., If it is null then its output true(Doesn't have value), if it is not null then it outputs false(Have value).

![](/logic_nodes/img/is-none.JPG)


### Is Not None

Give opposite bool value of null i.e., If it is not null then its output true(Have value), if it is null then it output false(Doesn't have value).

![](/logic_nodes/img/is-not-none.JPG)


### Loop

It is basically for(i in from...to) loop. "Index" give value specified by the index value."Done" is called when it is done looping.

![](/logic_nodes/img/Loop.JPG)


### Loop Break

Loop Break terminates loop containing it.

![](/logic_nodes/img/loop-break.JPG)


### Merge

The "New" button creates new inputs, the "X" one deletes the most bottom one. If it receives on activation from any of its inputs, it will activate its output.

![](/logic_nodes/img/Merge.JPG)


### Not

Inverts a plugged in boolean, so if its input is "true" it outputs "false".

![](/logic_nodes/img/Not.JPG)


### Sequence

Its call output in sequential order.

![](/logic_nodes/img/Sequence.JPG)


### Switch

Check the value on input “in”, When the input value matches Case1, Case 2 or Case 3 value, it will trigger the corresponding output Case 1, Case 2 or Case 3. Click "new" to add more Case Value.

![](/logic_nodes/img/Switch.JPG)


### To Bool

Is false when there is no event on input, true when there is an event on input.

![](/logic_nodes/img/to-bool.JPG)


### While

Its loop through as long as bool specified in "Condition" is same.(i.e., like  while(jumping == true){do domething}).

![](/logic_nodes/img/While.JPG)


### Sleep

Activates the node connected with its output after the float value in seconds after it was activated itself.

![](/logic_nodes/img/sleep.JPG)


## Event

### On Event

Activates the node\(s\) being connected to Sent Event or Sent Global Event specified in other node\(s\) tree.

![](/logic_nodes/img/on-event.JPG)


### On Init

Activates the node\(s\) being connected to it on the first frame of the game.

![](/logic_nodes/img/On-Init.JPG)


### On Timer

Activates the node\(s\) being connected to after a Timer countdown on from the beginning of the game, repeatedly when box ticked.

![](/logic_nodes/img/On-Timer.JPG)


### On Update

Activates the node\(s\) being connected to it every frame.

![](/logic_nodes/img/On-Update.JPG)


### On Volume Trigger

The lower object-input is used as Volume, the upper one as object-input for the object that enters/leaves/overlaps with it. 

Enter-mode: Activates the connected nodes on the frame the object enters the volume, on all other frames it doesn't do that.

Leave-mode: Activates the connected nodes on the frame the object leaves the volume, on all other frames it doesn't do that.

Overlap-mode: Activates the connected nodes on the frame the object overlaps with the volume, on all other frames it doesn't do that.

![](/logic_nodes/img/on-volume-trigger.JPG)


## Activators


### On Mouse

Activates the node\(s\) being connected to it when the set Mouse-button is being started, held down or released, depending on settings.

![](/logic_nodes/img/On-Mouse.JPG)


### On Keyboard

Activates the node\(s\) being connected to it when the set Keyboard-button is being started, held down or released, depending on settings.

![](/logic_nodes/img/On-Keyboard.JPG)



## States

### Mouse

Outputs a bool if the set button is being currently started, hold down, released, moved \(true\) or not \(false\).

![](/logic_nodes/img/Mouse.JPG)


### Mouse Cords

Outputs the X, Y location of the mouse of screen and its movement as Vector, and an integer if the scroll wheel es been moved up \(1\) or moved down \(-1\) this frame.

![](/logic_nodes/img/Mouse-Cords.JPG)


### Keyboard

Outputs a bool if the set button is being currently started, hold down, released, \(true\) or not \(false\).

![](/logic_nodes/img/Keyboard.JPG)


### Get Transform

Outputs the current transform of the set object. An objects Transform consists out of Vectors for its global location, rotation, and scale.

![](/logic_nodes/img/get-transform.JPG)


### Get Location

Outputs the current global location of the set object as vector.

![](/logic_nodes/img/get-location.JPG)


### Get Rotation

Outputs the current rotation of the set Object as a Vector.

![](/logic_nodes/img/get-rotation.JPG)


### Get Scale

Outputs the current scale of the set object as vector.

![](/logic_nodes/img/get-scale.JPG)


### Get Object

Searches for an object with the set name in the scene and outputs it.

![](/logic_nodes/img/get-object.JPG)


### Get Visible

Outputs a Boolean Value according to the objects current visibility setting in the Outliner. False if invisible, True if visible, even if the Object is not on camera right now.

![](/logic_nodes/img/get-visible.JPG)


### Get Child

Searches for object with the set name that is currently a child of the set object and outputs it.

![](/logic_nodes/img/get-child.JPG)


### Get Children

Outputs all current children of the set object as array of objects.

![](/logic_nodes/img/get-children.JPG)


### Get Parent

Outputs the current closest parent of the set object.

![](/logic_nodes/img/get-parent.JPG)


### Get Group

Searches for a group of objects with the set name and outputs it as an array of objects.

![](/logic_nodes/img/get-group.JPG)


### Group

Outputs all objects in the set group as array.

![](/logic_nodes/img/group.JPG) 


### Get Distance

Outputs the current distance between the two set objects as float.

![](/logic_nodes/img/get-distance.JPG)


### Get Trait

Searches for a Trait with the set name which is applied on the set object and outputs it.

![](/logic_nodes/img/get-trait.JPG)


### Active Camera

Outputs the current active Camera in your game as object.

![](/logic_nodes/img/active-camera.JPG)


### Active Scene

Outputs the currently active scene in your game.

![](/logic_nodes/img/active-scene.JPG)


### Volume Trigger

The lower object-input is used as Volume, the upper one as object-input for the object that enters/leaves/overlaps with it.

Enter-mode: Outputs true on the frame the object enters the volume, on all other frames it outputs false.

Leave-mode: Outputs true on the frame the object leaves the volume, on all other frames it outputs false.

Overlap-mode: Outputs true on the frames the object overlaps with the volume, on all other frames it outputs false.

![](/logic_nodes/img/Volume-trigger.JPG)


## Values

### Get Property

Can be used to receive Properties of other objects, which were set with the "[Set Property](/logic-nodes/set-property.md)" node. The properties name and object have to match the inputs of this node.

![](/logic_nodes/img/Get-property.JPG)


## Variables

### Action

TBD

![](/logic_nodes/img/Action.JPG)


### Boolean

Stores a Boolean value. A Boolean value has just two states: True and False.

![](/logic_nodes/img/boolean.JPG)


### Colour

Store colour value in RGB/HSV/HEX format.
 
![](/logic_nodes/img/Colour.JPG)

 
### Dynamic

TBD
 
![](/logic_nodes/img/Dynamic.JPG)  


### Float

Stores a Float value. A Float variable is a number with a limited number of decimals. If your number has more than 3 decimals, the value displayed will be rounded, but when you click on it you can still see the whole number, which will also be used in the game.

![](/logic_nodes/img/float.JPG)


### Global Object

Gives access to an global Object, which can be used to share information between different Traits.

![](/logic_nodes/img/global-object.JPG)


### Group

Get value stored in a group (Under Object tab) in Array form.

![](/logic_nodes/img/Group.JPG)


### Integer

Stores an integer value. These are whole numbers.

![](/logic_nodes/img/Integer.JPG)


### Material

Get material of any object specified.

![](/logic_nodes/img/Material.JPG)


### Mesh

Get reference of mesh specified.

![](/logic_nodes/img/Mesh.JPG)


### Object

Get reference any object specified.

![](/logic_nodes/img/Object.JPG)


### Quaternion

Store quaternion value.

![](/logic_nodes/img/Quaternion.JPG)


### Scene

Get reference of scene specified.

![](/logic_nodes/img/Scene.JPG)


### Scene Root

TBD

![](/logic_nodes/img/scene-root.JPG)


### String

Store string value.

![](/logic_nodes/img/String.JPG)


### Trait

Get reference of trait specified.

![](/logic_nodes/img/Trait.JPG)


### Transform

Store Location, Rotation, Scale value in vector form.

![](/logic_nodes/img/Transform.JPG)


### Vector

Store X, Y, Z value in vector.

![](/logic_nodes/img/Vector.JPG)


## Actions

### Set Variable

When activated, updates the first plugged in Variable to the Value of the second. Automatically converts some variable types.

![](/logic_nodes/img/set-variable.JPG)


### Translate Object

Moves the set object every frame it is activated by the given Vector.

![](/logic_nodes/img/translate-object.JPG)

### Set Property

When activated, sets or updates a Property of the given object named after its string input to the Value of its general Variable input \(the green one\). You do not have to worry about the variable type, you can plug everything it apart from activations. 

This node can be used to share Variables between different Traits. If the trait\(s\) you want to access the variable with are on different objects, use the "[Global Object](/logic-nodes/global-object.md)" node to store the data. Every trait can access this one.

![](/logic_nodes/img/set-property.JPG)


## Physics

### Apply Force

This apply force to the object assigned, where "Force", is direction force is applied in term of Vector.

![](/logic_nodes/img/apply-force.JPG)


### Apply Force at Location

This applies force to the object assigned, where "Force", is direction force is applied in term of Vector, and where "Location", is the location of the object where force is applied from in term of Vector.

![](/logic_nodes/img/apply-force-at-location.JPG)


### Apply Impulse

This apply impulse to the object assigned, where "Impulse", is direction force is applied in term of Vector.

![](/logic_nodes/img/apply-impulse.JPG)


### Apply Impulse at Location

This applies force to the object assigned, where "Impulse", is direction force is applied in term of Vector, and where "Location", is the location of the object where force is applied from in term of Vector.

![](/logic_nodes/img/apply-impulse-at-location.JPG)


### Cast Physics Ray

This cast physics ray from vector assigned to "From", to vector assigned to "To". "Hit" give the location of an object(object assigned to "Object") it hit to in term of vector.

![](/logic_nodes/img/cast-physics-ray.JPG)


### Get Contacts

This Get contacts of the object with item in the array.

![](/logic_nodes/img/get-contacts.JPG)


### Get First Contact

This Get contact of the object with another object that is assigned with the connector.

![](/logic_nodes/img/get-first-contact.JPG)


### Get Gravity

This Get gravity of an object in term of vector.

![](/logic_nodes/img/get-gravity.JPG)


### Get Velocity

This Get Linear and Angular velocity of an object in term of vector.

![](/logic_nodes/img/get-velocity.JPG)


### Has Contact

This gives bool value of contact between two objects that are assigned,i.e., If both objects contact each other than this gives True, and if not it gives False.

![](/logic_nodes/img/has-contact.JPG)


### On Contact

Contact between two objects that are assigned to:
1) Overlaps - When this two object completely overlap each other, then the "Out" connector is called.
2) End - When this two objects contact ends, then the "Out" connector is called.
3) Begins - When this two objects first contact, then the "Out" connector is called.

![](/logic_nodes/img/on-contact.JPG)


### Pick Object

When the object that is assigned to is in "Screen Coords" (Screen coord is coordination of screen in (X, Y) in term of vector. Note: "Z" is not used and should be ignored because we don't have 3D screen.) and then "Hit" is called to do something to it.

![](/logic_nodes/img/pick-object.JPG)

### Set Gravity

On activated, this set gravity in term of vector.

![](/logic_nodes/img/set-gravity.JPG)


### Set Velocity

On activated, this set:
1) The linear velocity of the object that is assigned to.
2) Linear Factor velocity of the object that is assigned to.
3) The angular velocity of the object that is assigned to.
4) Angular Factor velocity of the object that is assigned to.
In term of vector.

![](/logic_nodes/img/set-velocity.JPG)


## Sound

Note: Different between Pause Speaker and Stop Speaker, is that Pause speaker will just pause the speaker and can be resumed by Play Speaker. While Stop Speaker will completely stop it and cannot be resumed by Play Speaker, on doing so the speaker will play sound/music from start.

### Pause Speaker

On activating this pause speaker(Object that is assigned to as speaker) from playing sound.

![](/logic_nodes/img/pause-speaker.JPG)


### Play Sound

On activated this play sound/music that is assigned to.

![](/logic_nodes/img/play-sound.JPG)


### Play Speaker

On activated this start speaker(Object that is assigned to as speaker) to play sound.

![](/logic_nodes/img/play-speaker.JPG)


### Stop Speaker

On activated this stop speaker(Object that is assigned to as speaker) to stop playing sound.

![](/logic_nodes/img/stop-speaker.JPG)


## Canvas

Note: To get the canvas, be sure that the node\(s\) and the canvas(UI) is attached to the same object.

### Canvas Set Text

On activated it changes the text of element(button, label, etc.).

![](/logic_nodes/img/canvas-set-text.JPG)
