# Logic Nodes (Visual Scripting)

There are two option for scripting in Armory:
* Haxe
* Logic Nodes

Logic Nodes or visual scripting is full-fledged(It lack lot of features for now) scripting system based on nodes interface in Armory3D.
It can be used to used to create complex gameplay, This is ideal for people who don't have much programming experience.
It use Haxe Programming Language under the hood and Python for it UI.
You might be comfortable using Logic Nodes if you have good knowledge of blender and might have previously used Blender Game Engine or Unreal Engine 4.

Below is a screenshot of what Logic Nodes look like:

![](/assets/logic_nodes_nodesgrouplook.JPG)

As Armory3D is "Open-Source" 3D game enigne, It is possible for anybody to create their own Logic Node.
If you want to learn about how to create your own Logic Nodes, then follow this link ->[Custom Logic Nodes](/dev/logicnodes.md).

Now, let study about it!

![](/assets/.JPG)

White: This can be either float or string.

Red: In and Out Socket. This is connected to other logic nodes, it handle execution order.

Orange: Array. This is Array and it value.

Yellow: Bool. This is Boolean value such as True/False.

Darker Green: Integer. This is Integer value such as -8 or 8.

Green: Transform. This is Transform value such as Location, Rotaion, Scale.

Purple: Vector. This is Vector value such as X-Axis, Y-Axis, Z-Axis.

Blue: Object. This is reference of Object.

## There are 13 different Logic Nodes group:

Action: This Logic node group handle action, i.e., what it should, what action it should take. For simpilcity sake, Action Logic Nodes Documentaion is divided into 2 parts. 
Follow this link to know more about it -> [Action(Part-I)](/logic_nodes/logic_nodes_action1.md) [Action(Part-II)](/logic_nodes/logic_nodes_action2.md).

Animation: This Logic Nodes group handles animation, i.e., it tell the object what animtion related thing it should do. 
Follow this link to know more about it -> [Animation](/logic_nodes/logic_nodes_animation.md).

Array: This Logic Nodes group handles arrays, arrays can be create for any type, i.e., Arrays can be created for objects, variables, and even sound!. 
Follow this link to know more about it -> [Array](/logic_nodes/logic_nodes_array.md)

Canvas: This Logic Nodes group handles canvas,i.e., handle the UI element that are in canvas. 
Follow this link to know more about it -> [Canvas](/logic_nodes/logic_nodes_canvas.md).

Event: This Logic Nodes group handle triggering of an event,i.e., what should be done when a particular event is triggered, such as what should be done when the object attached to is initialised, etc. 
Follow this link to know more about it -> [Event](/logic_nodes/logic_nodes_event.md).

Input: This Logic Nodes group handle input from players's controller, This get input from Keyboard, Mouse and Gamepad. 
Follow this link to know more about it -> [Input](/logic_nodes/logic_nodes_input.md).

Logic: This Logic Nodes group handle gameplay mechanism, i.e., logic of game. 
Follow this link to know more about it -> [Logic](/logic_nodes/logic_nodes_logic.md).

Native: This Logic Nodes group handle calls from native(Haxe Script), i.e., get function or call function from a haxe scipt. 
Follow this link to know more about it -> [Native](/logic_nodes/logic_nodes_native.md).

Navmesh: This Logic Nodes group handle Navigation Mesh, this group is used in helping AI(Artificial Intelligence) agent with pathfinding through complicated structures. 
Follow this link to know more about it -> [Navmesh](/logic_nodes/logic_nodes_navmesh.md).

Physics: This Logic Nodes group handle physics in gameplay, 
Follow this link to know more about it -> [Physics](/logic_nodes/logic_nodes_physics.md).

Sound: This Logic Nodes group help with sound system in game, i.e., when to play sound, where should sound play, etc. 
Follow this link to know more about it -> [Sound](/logic_nodes/logic_nodes_sound.md).

Value: This Logic Nodes group give value of specific thing of specific nodes, i.e., get trait of an object, get invisibility of an object, etc. For simpilcity sake, Value Logic Nodes Documentaion is divided into 2 parts. 
Follow this link to know more about it -> [Value(Part-I)](/logic_nodes/logic_nodes_value.md). [Value(Part-II)](/logic_nodes/logic_nodes_value.md).

Variables: This Logic Nodes group give all variable types, i.e., give value of Float, Int, Bool, and many more!.
[Variables](/logic_nodes/logic_nodes_variables.md).

Logic Pack Nodes: This Logic Nodes group are made by Armory community, this pack may have varying type of nodes. Follow this link to know more about it -> [Logic Pack Nodes](/logic_nodes/logic_nodes_logicpack.md).

### Example
Logic Node Example: [Example](/logic_nodes/temp.md).