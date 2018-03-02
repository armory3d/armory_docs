# Tutorial 5 - Logic

This page describes how to work with **logic node system** in Armory. Logic nodes provide a visual way of creating interactive scenes. When you build your project, created node trees are automatically compiled down to scripts.

## Node types

The whole system consists of just 5 essential categories.

- **Events** - nodes where execution starts, triggered by desired event

- **Actions** - once an event is triggered, these nodes take action

- **Logic** - nodes used to control execution flow, using branching, loops, gates..

- **Variables** - nodes used to store data in a logic tree

- **Values** - nodes used to retrieve data from other objects

## Hello world!

Let's craft the simplest example - after pressing down mouse button, we will show a 'Hello world' message. Start up with a default scene, switch to **Node Editor** area and select **Logic Nodes** type. Press **New** to create a new node tree.

You can browse all available nodes through **Add** menu item, or simply hit **Shift + A** to start searching. Search for **On Mouse** node and hit enter to place it. This is an event node that gets triggered when the mouse button is pressed. Next, place a **Print** node - an action node. Connect **Out** socket of the **On Mouse** node to the **In** socket of the **Print** node. As soon as the mouse gets pressed, **Print** node gets executed. Lastly, we need to tell the **Print** node what to print. Place a **String** node and set its value to 'Hello world!' - this is a variable node. Connect **String** and **Value** sockets.

Each node tree has to be attached to an object using a trait system. Similar to the materials defining object looks, logic tree defines its behaviour. Select cube and create new trait in *Properties - Object - Armory Traits*. Set type to Logic Nodes and enter our newly created node tree as Tree entry. That is it - press **P** to play in viewport and click the mouse in viewport area. You will notice a message in a viewport header.

![](/getting_started/img/scene5/1.jpg)

Using node tree it is easy to interact directly with cube object. Delete all nodes and start fresh. Place **On Mouse** node and switch the first property of **On Mouse** node to **Started**. This indicates that event will fire only once when mouse button changes from rest state to pressed state.

 Create **Translate Object** node and connect it to the **On Mouse** node. Notice that we leave the object field on **Translate Object** node blank - this will automatically select the trait owner - in out case the cube. Set **Vector Y** field to 2.0. Press P and click the mouse - cube object will move on every click.

![](/getting_started/img/scene5/2.jpg)

We can easily limit the maximum distance allowed the cube to translate. Insert a **Gate** node between **On Mouse** node and **Translate Object** node. Set its type to **Less**. Place a **Get Location** node - a value node. This will retrieve current location of cube object. Connect it to the **Separate XYZ** node. We want to limit the distance on Y axis - connect it to the first value socket of **Gate** node. Create **Float** - a variable node - and set it to 5.0. If you play the scene now, cube moves only 3 times and then stops.

Get the full blend for this example:
- https://github.com/armory3d/armory_examples/tree/master/logic_helloworld

![](/getting_started/img/scene5/3.jpg)

## Tanks

Grab some snack and sit tight - let's build an actual game prototype. The game will consist of 2 players handling a tank and battling each other. We build a small playground with obstacles and two tanks models. Each object has a rigid body set.

![](/getting_started/img/scene5/4.jpg)

Red tank acts as a player 1. We allow both keyboard and gamepad controls, but hard-code the actual keys used for simplicity. In a **Player1Controls** tree, the left key on keyboard or gamepad is set to send an event named **'turn_left'**. Later on, we use this event to rotate player controlled tank.

![](/getting_started/img/scene5/5.jpg)

Do this for all keys - left, right, forward and backward.

![](/getting_started/img/scene5/6.jpg)

Blue tank acts as a player 2. We define the same controls, but map the keys to WSAD and second connected gamepad instead.

![](/getting_started/img/scene5/7.jpg)

In a **TankTree**, we listen to the events and perform actions to actually control the tank. The reason this node tree is separate is that we attach it to both tanks, preventing any duplicated work.

**On Event** node is set to listen to the **'turn_left'** event. For player 1, this event is triggered when left key is pressed. For player 2, it happens on the A key press. **On Event** node is connected to the **Rotate Object** node, with **Vector Z** value set to a small positive value controlling the rotation speed. Playing the game now, pressing the left key rotates the tank! 

![](/getting_started/img/scene5/8.jpg)

We do the same for the **'turn_right'** event, however the **Vector Z** value is set to a negative value to rotate in the opposite direction.

![](/getting_started/img/scene5/9.jpg)

On to the handling **'forward'** event. To figure out which direction should the tank move in, **Vector from Transform** node is used with type set to **Look**. This vector is then scaled down using **Vector Math** node to slow down tank speed moving forward. Resulting vector is passed into **Translate Object** node.

![](/getting_started/img/scene5/10.jpg)

As before, we do the same for **'backward'** event with translate vector reversed.

![](/getting_started/img/scene5/11.jpg)

Now that the tanks are fully controllable, we make them shoot bullets. To keep scene clear, bullet object is placed in the second scene layer with **Render disabled**. This ensures object will be exported but not visible on its own.

![](/getting_started/img/scene5/12.jpg)

Selecting the red tank, an empty object is added as a child - the location of this object defines where to shoot bullets from. A new logic tree is added to this empty object. M key or gamepad cross/a key emits a **'fire'** event. We do the same for blue tank.

![](/getting_started/img/scene5/13.jpg)

We attach another logic tree - handling response to the **'fire'** event. We spawn a new object - our bullet model from layer 2, and set its location to the logic tree owner - in this case a bullet spawn point - defined as an empty object placed as a child of tank.

![](/getting_started/img/scene5/14.jpg)

Playing the scene now, we discover the bullets fall from the cannon down to the ground. We need some fire powder!

![](/getting_started/img/scene5/15.jpg)

**Apply Impulse** node fixes that. Similar to moving the tank forward, we acquire the forward vector and scale it up.

![](/getting_started/img/scene5/16.jpg)

Even though Armory culls out of screen objects, it is important to keep resources used down to a minimum. We remove each bullet after 2 seconds of lifetime. To do this, **Array(Object)** node is placed and all fired bullets are stored in this array using the **Array Add** node. We wait 2 seconds with **Sleep** node and call **Remove Object** node. **Array Shift** node feeds the first element from bullet array into the **Remove Object** node, and also removes this element from array itself.

![](/getting_started/img/scene5/17.jpg)

That's it - feel free to experiment further! Get the full blend for this example:

- https://github.com/armory3d/armory_examples/tree/master/tutorial5

The game can be instantly played in the browser (and all the other targets) - including gamepad support:
- http://armory3d.org/demo/scene5/

![](/getting_started/img/scene5/18.jpg)
