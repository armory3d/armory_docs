# Actions

## Set Variable

When activated, updates the first plugged in Variable to the Value of the second. Automatically converts some variable types.

![](/assets/set-variable.JPG)


## Translate Object

Moves the set object every frame it is activated by the given Vector.

![](/assets/translate-object.JPG)

## Set Property

When activated, sets or updates a Property of the given object named after its string input to the Value of its general Variable input \(the green one\). You do not have to worry about the variable type, you can plug everything it apart from activations. 

This node can be used to share Variables between different Traits. If the trait\(s\) you want to access the variable with are on different objects, use the "[Global Object](/logic-nodes/global-object.md)" node to store the data. Every trait can access this one.

![](/assets/set-property.JPG)