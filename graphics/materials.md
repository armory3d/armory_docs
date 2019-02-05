# Materials

![](/graphics/img/materials.jpg)

Materials are built with [Cycles nodes](https://docs.blender.org/manual/en/dev/render/cycles/nodes/index.html).

## Displacement

Locate the `Armory Render Path - Renderer - Displacement` property:
- `Off` - No displacement performed
- `Vertex` - Mesh vertices are displaced
- `Tessellation` - Mesh is first tessellated for more detail and then displaced

With `Tessellation` selected, the level of tessellation can be set using the `Mesh` and `Shadow` property.

Note: Vertices are displaced in normals direction. Use smooth shading (`Space - Shade Smooth`) for meshes with displacement to prevent gabs.

Examples:
- https://github.com/armory3d/armory_examples/tree/master/material_examples

## Blending

To enable additive blending for specific material, set `Armory Render Path - Blending` to `On` and check the `Blending` property in `Material - Armory Props`.

Examples:
- https://github.com/armory3d/armory_examples/tree/master/material_translucent
- https://github.com/armory3d/armory_examples/tree/master/particle_examples

## Material parameters

`RGB`, `Value` and `Image Texture` material nodes can be controlled at run-time using script or logic nodes. To expose material node, enable `Parameter` property in `Node Editor - Properties - Armory Material Node`.

Examples:
- https://github.com/armory3d/armory_examples/tree/master/material_params
