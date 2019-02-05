# Global Illumination

This page presents a quick start guide to let you easily **setup global illumination** in your Armory projects.

Armory features a fully dynamic global illumination technique based on a combination of voxel cone-tracing and screen-space ray-tracing. First, the scene is voxelized and processed into a 3D texture. This data is then used to gather coarse lighting of the scene. Afterwards, screen-space ray-tracing is performed for detail.

- Get the teapots [.blend scene](https://github.com/armory3d/armory_examples/tree/master/voxelgi_teapots) (troll not included!).

<iframe width="560" height="315" src="https://www.youtube.com/embed/8KavBpfLLtY?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Requirements

- A graphics card with **OpenGL 4.4** or **Direct3D 11** support (for voxelization).
- Runs on **Windows** and **Linux**.

## Voxel AO

Set `Armory Render Path - Voxels - Global Illumination` to `Voxel AO`.

The cheapest way of utilizing voxels, usable for **ambient occlusion and shadows**. Runs faster and consumes less memory compared to `Voxel GI`.

- Control the quality using the `Cones` property.
- Control the intensity using the `Occlusion` property.
- Tweak tracing parameters using the `Step, Range, Offset` properties.

<div style="width:50%">![](/graphics/img/gi/ao.jpg)</div>

## Voxel GI

Set `Armory Render Path - Voxels - Global Illumination` to `Voxel GI`.

Voxel GI enables **indirect diffuse and specular lighting**. This is a performance heavy feature and should be enabled only on higher-end hardware. Flickering or leaks can occur.

- Control the quality using the `Cones` property.
- Control the intensity using the `Diffuse, Specular, Occlusion` properties.
- Tweak tracing parameters using the `Step, Range, Offset` properties.
- Control environment map contribution to indirect lighting using `Env Map` property.

<div style="width:50%">![](/graphics/img/gi/game.jpg)</div>

## Voxel Volume Setup

Locate `Armory Render Path - Voxels` panel. When set to `Voxel AO` or `Voxel GI`, **voxelization volume** can be configured. 

- Adjust `Dimensions` to control the volume size. Objects placed out of this volume will not contribute to global illumination. By default, dimensions are set to 16 - meaning a volume of 16x16x16 blender units gets voxelized.
- Set `Resolution` to specify amount of voxels used for the volume. For performance, keep this at 128 or below.
- Reduce the `Resolution Z` multiplier to conserve memory if your scene is mostly flat on the Z axis (like a chess board). With `Resolution Z` set to 0.5, 16x16x8 dimensions will get voxelized.
- Enable `Revoxelize` property to update voxel volume every frame. In case of mostly static scenes, you can keep this off - moving objects will receive indirect lighting, but will not affect it. To prevent object from contributing into indirect lighting, enable `Properties - Object - Armory Props - Mobile`.
- With `Revoxelize` checked, enable `Dynamic Camera` to voxelize scene around the camera. As the camera moves, voxelization volume will move as well, making it possible to cover infinitely big scenes. With `Dynamic Camera` disabled, the volume at the scene origin(0,0,0) gets voxelized.
- `Relight` property will allow the voxel volume to be recomputed when light transform changes.
- `Temporal Filter` will blend the indirect lighting with results from the previous frame, in order to minimize flickering.

## Screen-space ray-tracing

### Ray-traced AO

Set `Armory Render Path - SSGI` to `RTAO`.

**Ambient occlusion** will be traced.

- Control the quality using the `Rays, Step, Max Steps` properties.
- Control the intensity using the `Strength` property.

### Ray-traced GI

Set `Armory Render Path - SSGI` to `RTGI`.

**Indirect diffuse lighting** will be traced.

- Control the quality using the `Rays, Step, Max Steps` properties.
- Control the intensity using the `Strength` property.

### Ray-traced Shadows

Small scale **contact shadows** will be traced.

Enable `Armory Render Path - SSRS`.

- Increase `Step` in case of artefacts.

### Ray-traced Reflections

**Local reflections** will be traced.

Enable `Armory Render Path - SSR`.

- Increase `Step` in case of artefacts.

## Baked lighting

Blender has a full path-tracing Cycles engine integrated. For static scenes, you can pre-bake lighting down into lightmaps using the built-in `Armory Bake` tool.

- Locate `Properties - Render - Armory Bake` panel.
- Add objects to be baked or click `Triangle - Add All`.
- Hit `Bake` to generate lightmaps for all listed objects.
- Once done, hit `Apply` to restore materials and pack lightmaps.
- Optionally, set `Armory Render Path - Preset` to `2D/Baked`.
- Run(F5)! Armory picks up baked materials.


- Get [example .blend scene](https://github.com/armory3d/archviz_templates/tree/master/baked).

## Light probes

Currently supported light probe features:

- See [example](https://github.com/armory3d/armory_examples/tree/master/light_probes)
