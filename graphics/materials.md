# Materials

<img src="./graphics/img/materials.jpg">

*Draft*

Materials are built with [Cycles nodes](https://docs.blender.org/manual/en/dev/render/cycles/nodes/index.html).

## Displacement

Locate the `Armory Render Path - Renderer - Displacement` property:
- `Off` - No displacement performed
- `Vertex` - Mesh vertices are displaced
- `Tessellation` - Mesh is first tessellated for more detail and then displaced

With `Tessellation` selected, the level of tessellation can be set using the `Mesh` and `Shadow` property.

Note: Vertices are displaced in normals direction. Use smooth shading (`Space - Shade Smooth`) for meshes with displacement to prevent gabs.

When using a height texture map, you can place an `Armory PBR` node and connect the height map to the `Height` socket. Make sure to also connect the `Displacement` sockects.

<img src="./graphics/img/displace.png">

Examples:
- https://github.com/armory3d/armory_examples/tree/master/material_displace
- https://github.com/armory3d/armory_examples/tree/master/material_tessellation
