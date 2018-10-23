# Reference

## Activators

### On Init

Activates the node\(s\) being connected to it on the first frame of the game.

![](/assets/On-Init.JPG)


### On Timer

Activates the node\(s\) being connected to after a Timer countdown on from the beginning of the game, repeatedly when box ticked.

![](/assets/On-Timer.JPG)


### On Mouse

Activates the node\(s\) being connected to it when the set Mouse-button is being started, held down or released, depending on settings.

![](/assets/On-Mouse.JPG)


### On Keyboard

Activates the node\(s\) being connected to it when the set Keyboard-button is being started, held down or released, depending on settings.

![](/assets/On-Keyboard.JPG)


### On Update

Activates the node\(s\) being connected to it every frame.

![](/assets/On-Update.JPG)


### On Volume Trigger

The lower object-input is used as Volume, the upper one as object-input for the object that enters/leaves/overlaps with it. 

Enter-mode: Activates the connected nodes on the frame the object enters the volume, on all other frames it doesn't do that.

Leave-mode: Activates the connected nodes on the frame the object leaves the volume, on all other frames it doesn't do that.

Overlap-mode: Activates the connected nodes on the frame the object overlaps with the volume, on all other frames it doesn't do that.

![](/assets/on-volume-trigger.JPG)


## Logic

### Array loop

Its loop through each item assingned in array."Value" give item specified by index's value."Done" calls connectors when its is done looping through array.

![](/assets/array-loop.JPG)


### Loop

Its is basically for(i in from...to) loop. "Index" give value specified by index value."Done" is called when it is done looping.

![](/assets/Loop.JPG)

### Alternate

Alternates between its activated outputs to pass through its input when it is being re-activated.  

![](/assets/Alternate.JPG)


### Gate

Logic nodes way to do "if" statements. When activated, it compares if its two inputs are being Equal, Greater Equal, Less Equal, or Not Equal, regardless of variable type, and passes through its red input if the set state is the case.

"And" and "Or" are being used for booleans only, and pass through the input when both bools are true \(and\) or at least one \(or\).

![](/assets/Gate.JPG)


### Is None

Give bool value of null i.e., If it is null then its output true(Doesn't have value), if it is not null then it output false(Have value).

![](/assets/is-none.JPG)


### Is Not None

Give opposite bool value of null i.e., If it is not null then its output true(Have value), if it is null then it output false(Doesn't have value).

![](/assets/is-not-none.JPG)


### Sequence

Its call output in sequential order.

![](/assets/Sequence.JPG)


### While

Its loop through as long as bool specified in "Condition" is same.(i.e., like  while(jumping == true){do domething}).

![](/assets/While.JPG)


### Not

Inverts a plugged in boolean, so if its input is "true" it outputs "false".

![](/assets/Not.JPG)


### Sleep

Activates the node connected with its output after the float value in secounds after it was activated itself.

![](/assets/sleep.JPG)


### Branch

When activated, activates its "True" or "False" output, according to the state of the plugged in boolean.

![](/assets/Branch.JPG)


### Is True/False

Passes through its activation only if the plugged in boolean is "True"/"False", according to the node.![](/assets/Is-true_false.JPG)


### Merge

The "New" button creates new inputs, the "X" one deletes the most bottom one. If it receives on activation from any of its inputs, it will activate its output.

![](/assets/Merge.JPG)

## States

### Mouse

Outputs a bool if the set button is being currently started, hold down, released, moved \(true\) or not \(false\).

![](/assets/Mouse.JPG)


### Mouse Cords

Outputs the X,Y location of the mouse on screen and its movement as Vector, and an integer if the scroll wheel es been moved up \(1\) or moved down \(-1\) this frame.

![](/assets/Mouse-Cords.JPG)


### Keyboard

Outputs a bool if the set button is being currently started, hold down, released, \(true\) or not \(false\).

![](/assets/Keyboard.JPG)


### Get Transform

Outputs the current transform of the set object. An objects Transform consists out of Vectors for its global location, rotation and scale.

![](/assets/get-transform.JPG)


### Get Location

Outputs the current global location of the set object as vector.

![](/assets/get-location.JPG)


### Get Rotation

Outputs the current rotation of the set Object as a Vector.

![](/assets/get-rotation.JPG)


### Get Scale

Outputs the current scale of the set object as vector.

![](/assets/get-scale.JPG)


### Get Object

Searches for an object with the set name in the scene and outputs it.

![](/assets/get-object.JPG)


### Get Visible

Outputs a Boolean Value according to the objects current visibility setting in the Outliner. False if invisible, True if visible, even if the Object is not on camera right now.

![](/assets/get-visible.JPG)


### Get Child

Searches for object with the set name that is currently a child of the set object and outputs it.

![](/assets/get-child.JPG)


### Get Children

Outputs all current children of the set object as array of objects.

![](/assets/get-children.JPG)


### Get Parent

Outputs the current closest parent of the set object.

![](/assets/get-parent.JPG)


### Get Group

Searches for a group of objects with the set name and outputs it as an array of objects.

![](/assets/get-group.JPG)


### Group

Outputs all objects in the set group as array.

![](/assets/group.JPG) 


### Get Distance

Outputs the current distance between the two set objects as float.

![](/assets/get-distance.JPG)


### Get Trait

Searches for a Trait with the set name which is applied on the set object and outputs it.

![](/assets/get-trait.JPG)


### Active Camera

Outputs the current active Camera in your game as object.

![](/assets/active-camera.JPG)


### Active Scene

Outputs the currently active scene in your game.

![](/assets/active-scene.JPG)


### Volume Trigger

The lower object-input is used as Volume, the upper one as object-input for the object that enters/leaves/overlaps with it.

Enter-mode: Outputs true on the frame the object enters the volume, on all other frames it outputs false.

Leave-mode: Outputs true on the frame the object leaves the volume, on all other frames it outputs false.

Overlap-mode: Outputs true on the frames the object overlaps with the volume, on all other frames it outputs false.

![](/assets/Volume-trigger.JPG)


## Values and Variables

### Global Object

Gives access to an global Object, which can be used to share information between different Traits.

![](/assets/global-object.JPG)


### Get Property

Can be used to receive Properties of other objects, which were set with the "[Set Property](/logic-nodes/set-property.md)" node. The properties name and object have to match the inputs of this node.

![](/assets/Get-property.JPG)


### Integer

Stores an integer value. These are whole numbers.

![](/assets/Integer.JPG)


### Float

Stores a Float value. A Float variable is a number with a limited number of decimals. If your number has more than 3 decimals, the value displayed will be rounded, but when you click on it you can still see the whole number, which will also be used in the game.

![](/assets/float.JPG)


### Boolean

Stores a Boolean value. A Boolean value is has just two states: True and False.

![](/assets/boolean.JPG)


## Actions

### Set Variable

When activated, updates the first plugged in Variable to the Value of the second. Automatically converts some variable types.

![](/assets/set-variable.JPG)


### Translate Object

Moves the set object every frame it is activated by the given Vector.

![](/assets/translate-object.JPG)

### Set Property

When activated, sets or updates a Property of the given object named after its string input to the Value of its general Variable input \(the green one\). You do not have to worry about the variable type, you can plug everything it apart from activations. 

This node can be used to share Variables between different Traits. If the trait\(s\) you want to access the variable with are on different objects, use the "[Global Object](/logic-nodes/global-object.md)" node to store the data. Every trait can access this one.

![](/assets/set-property.JPG)
