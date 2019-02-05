# Physics

Armory is designed to work with any physics engine. Internally, a glue code is written which binds the physics simulation. This lets you pick the most suitable physics engine depending on project needs and makes Armory future-proof.

If no rigid body is detected in the scene, Armory skips including the physics module to save space and performance. To force the physics module, set `Armory Project - Modules - Physics` from `Auto` to `Enabled`.

By default, Armory is configured to use a full featured [Bullet physics](https://github.com/armory3d/haxebullet). If lighter engine is sufficient, [Oimo physics](https://github.com/armory3d/oimo_module) is provided. With Oimo, triangle mesh shapes are approximated using convex hulls.

To pick active physics engine, set `Armory Project - Modules - Physics Engine` property.
