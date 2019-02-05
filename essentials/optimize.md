# Optimize

Armory is designed to automatically strip away unused features from exported projects to prevent size and performance bloat. This page discusses options to fine-tune this process.

## Build times

To keep the builds times low:
- Enable `Khamake Threads` in Armory add-on preferences
- Enable `Compilation Server` in Armory add-on preferences
- Enable `Armory Project - Flags - Cache Build`

`Khamake Threads` will enable multi-threaded shader/asset compiling. `Compilation Server` will allow Haxe to compile faster. `Cache Build` will allow Armory to reuse data from previous compilation.

Depending on the CPU, the repeated builds of scenes like the [first_person](https://github.com/armory3d/armory_templates/tree/master/first_person) template should fit into one second.

## Optimize for size

- Enable `Armory Exporter - DCE`
- Enable `Armory Exporter - Optimize Data`
- Enable `Armory Exporter - Asset Compression`
- Disable `Armory Exporter - Compiler Inline`
- Enable `Armory Project - Flags - Minimize Data`
- If unused, disable `Armory Project - Modules - Audio`

Inspect `Armory Render Path` to ensure features which are not in use are off. Disabling particles, skinning, shadows, decals, translucency or certain post-processing features will bring the size further down.

Use `Armory Exporter - Publish` to export the project. This will allow compiler to perform DCE (dead code elimination).

For Krom/HTML5 targets, use a tool like [jscompress.com](https://jscompress.com/) to minify `krom.js`/`kha.js` files. With all the options tweaked for size, default scene containing a single cube should fit into 240KB/57KB(zip) using a mobile render path.

Armory supports multiple physics engines - see [oimo_module](https://github.com/armory3d/oimo_module) for lightweight alternative to Bullet.

## Optimize for performance

- Enable `Armory Exporter - Optimize Data`
- Enable `Armory Exporter - Compiler Inline`
- Enable `Armory Project - Minimize Data`
- Enable `Armory Project - Flags - Batch Meshes` (experimental)
- Enable `Armory Project - Flags - Batch Materials` (experimental)

General engine performance will mainly depend on the render path. `Armory Render Path` panel allows you to create several render paths, each targeting a different platform/setup. Based on whether the game is CPU or GPU bound, features like skinning or particles can be set to calculate either on CPU or GPU.
