# Navmesh

Armory is designed to work with any navigation engine. Internally, a glue code is written which binds the engine. By default, Armory is configured to use [Recast navigation](https://github.com/armory3d/haxerecast).

If no navmesh is detected in the scene, Armory skips including the navmesh module to save space and performance. To force including the module, set `Armory Project - Navigation` from `Auto` to `Enabled`.

To auto-generate navmesh from existing mesh, hit `Properties - Scene - Armory Navigation - Generate Navmesh`.

Examples:
- https://github.com/armory3d/armory_examples/tree/master/navmesh
