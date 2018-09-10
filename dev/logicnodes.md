# Logic Nodes

## Creating custom nodes

### Create a library

We will make a new library to store the sources of custom logic nodes and keep them portable with no modifications to engine sources.

Locate your blend file and create a new `Libraries` folder alongside it. Navigate to the `Libraries` folder and create a new `mynodes` folder in it.

### Python

Start by creating the logic node definition for Blender. Create a file named `blender.py` in `Libraries/mynodes` folder. Armory automatically picks this file up once the library is loaded. Define a simple node with single in/out socket.

```py
from bpy.types import Node
from arm.logicnode.arm_nodes import *
import arm.nodes_logic

class TestNode(Node, ArmLogicTreeNode):
    '''Test node'''
    bl_idname = 'LNTestNode'
    bl_label = 'Test'
    bl_icon = 'GAME'

    def init(self, context):
        self.inputs.new('ArmNodeSocketAction', 'In')
        self.outputs.new('ArmNodeSocketAction', 'Out')

def register():
    # Add custom nodes
    add_node(TestNode, category='Action')
    # Register newly added nodes
    arm.nodes_logic.register_nodes()
```

Restarting Blender and loading the project again, the new logic node is available for placement.

![](/dev/img/logicnodes/1.png)

### Haxe

Before the project can be run, we need to implement the actual node logic in Haxe. When the node gets executed, we let it print a 'Hello, World!' string.

```haxe
package armory.logicnode;

class TestNode extends LogicNode {

	public function new(tree:LogicTree) {
		super(tree);
	}

	override function run() {
		// Logic for this node
		trace("Hello, World!");

		// Execute next action linked to this node
		super.run();
	}
}
```

Done!

### Where to next

- Example project:
https://github.com/armory3d/armory_examples/tree/master/dev_logicnode

- Example on adding a `Contains String` node into Armory:
https://github.com/armory3d/armory/commit/094c0e9597023025eca525d173e6f6d29b5201b6

When implementing new logic nodes, it is easy to browse the sources of existing nodes as a reference.

- Python definitions of Armory nodes:
https://github.com/armory3d/armory/tree/master/blender/arm/logicnode

- Haxe counterparts:
https://github.com/armory3d/armory/tree/master/Sources/armory/logicnode
