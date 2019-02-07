# Tanks Game

<iframe width="560" height="315" src="https://www.youtube.com/embed/5b97eR5_fQI?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Let's build a mini-game! It will consist of 2 players handling a tank and battling each other. We build a small playground with obstacles and two tanks models. Each object has a rigid body set. Some of the obstacles are animated on the timeline to make the game more dynamic. The lighting setup is based on the [Playground tutorial](/getting_started/playground.md).

![](/getting_started/img/tanks/0.jpg)

Red tank acts as a player 1. We allow both keyboard and gamepad controls, but hard-code the actual keys used for simplicity. In a **Player1Controls** tree, the left key on keyboard or gamepad is set to send an event named **'turn_left'**. Later on, we use this event to rotate the player controlled tank.

![](/getting_started/img/tanks/1.jpg)

Do this for all keys - left, right, forward and backward.

![](/getting_started/img/tanks/2.jpg)

Blue tank acts as a player 2. We define the same controls, but map the keys to WSAD and the second connected gamepad instead.

In a **TankTree**, we listen to the events and perform actions to actually control the tank. The reason this node tree is separate is that we attach it to both tanks, preventing duplicated node trees.

**On Event** node is set to listen to the **'turn_left'** event. For player 1, this event is triggered when left key is pressed. For player 2, it happens on the A key press. **On Event** node is connected to the **Rotate Object** node, with **Vector Z** value set to a small positive value controlling the rotation speed. Playing the game now, pressing the left key rotates the tank! 

![](/getting_started/img/tanks/3.jpg)

We do the same for the **'turn_right'** event, however the **Vector Z** value is set to a negative value to rotate in the opposite direction.

On to the handling **'forward'** event. To figure out which direction should the tank move in, **Vector from Transform** node is used with type set to **Look**. This vector is then scaled down using **Vector Math** node to slow down tank speed moving forward. Resulting vector is passed into **Translate Object** node.

![](/getting_started/img/tanks/4.jpg)

As before, we do the same for **'backward'** event with translate vector reversed.

Now that the tanks are fully controllable, we make them shoot bullets. To keep scene clear, bullet object is placed in separate collection with **Render** icon disabled. This ensures object will be exported but not visible on its own.

![](/getting_started/img/tanks/5.jpg)

Selecting the red tank, an empty object is added as a child - the location of this object defines where to shoot bullets from. A new logic tree is added to this empty object. M key or gamepad cross/a key emits a **'fire'** event. We do the same for blue tank.

![](/getting_started/img/tanks/6.jpg)

We attach another logic tree - handling response to the **'fire'** event. We spawn a new object - our bullet model from layer 2, and set its location to the logic tree owner - in this case a bullet spawn point - defined as an empty object placed as a child of tank.

![](/getting_started/img/tanks/7.jpg)

Playing the scene now, we discover the bullets fall from the cannon down to the ground. We need some fire powder!

![](/getting_started/img/tanks/8.jpg)

**Apply Impulse** node fixes that. Similar to moving the tank forward, we acquire the forward vector and scale it up.

![](/getting_started/img/tanks/9.jpg)

Even though Armory culls out of screen objects, it is important to keep resources used down to a minimum. We remove each bullet after 2 seconds of lifetime. To do this, **Array(Object)** node is placed and all fired bullets are stored in this array using the **Array Add** node. We wait 2 seconds with **Sleep** node and call **Remove Object** node. **Array Shift** node feeds the first element from bullet array into the **Remove Object** node, and also removes this element from array itself.

![](/getting_started/img/tanks/10.jpg)

That's it - feel free to experiment further! Get the full blend for this tutorial:

- https://github.com/armory3d/armory_tutorials
