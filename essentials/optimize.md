# Optimize

Armory is designed to automatically strip away unused features from exported projects to prevent size and performance bloat. This page discusses options to fine-tune this process.

## Build times

To keep the builds times low:
- Enable `Khamake Threads` in Armory add-on preferences
- Enable `Armory Project - Cache Shaders`
- Enable `Armory Project - Cache Compiler`

`Khamake Threads` will enable multi-threaded shader/asset compiling. `Cache Shaders/Compiler` will allow Armory to reuse data from previouse compilation.

Depending on the CPU, the repeated builds of scenes like the [first_person](https://github.com/armory3d/armory_templates/tree/master/first_person) template should fit into one second.

## Optimize for size

- Enable `Armory Project - DCE`
- Enable `Armory Project - Minimize Data`
- Enable `Armory Project - Asset Compression`
- Disable `Armory Project - Compiler Inline`
- If unused, disable `Armory Project - Audio`

Inspect `Armory Render Path` to ensure features which are not in use are off. Disabling particles, skinning, shadows, decals, translucency or certain post-processing features will bring the size further down.

Use `Armory Exporter - Publish` to export the project. This will allow to perform DCE (dead code elimination).

For Krom/HTML5 targets, use a tool like [jscompress.com](https://jscompress.com/) to further minimize `krom.js`/`kha.js` files. Default scene containing a single cube should fit into 290KB/71KB(zip) using a low forward path.

Armory supports multiple physics engines - see [oimo_module](https://github.com/armory3d/oimo_module).

## Optimize for performance

- Enable `Armory Project - Minimize Data`
- Enable `Armory Project - Compiler Inline`
- Enable `Armory Project - Optimize Meshes`
- Enable `Armory Project - Batch Meshes` (experimental)
- Enable `Armory Project - Batch Materials` (experimental)

General engine performance will mainly depend on the render path. `Armory Render Path` panel allows you to create several render paths, each targeting a different platform/setup. Based on whether the game is CPU or GPU bound, features like skinning or particles can be set to calculate either on CPU or GPU.
