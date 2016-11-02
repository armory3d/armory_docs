## Anti-aliasing (AA)

Aliasing has a big impact on the image quality. To fight it, Armory comes pre-equipped with several solutions. Each has varying quality / performance ratio.

- [No AA](#no-aa)
- [MSAA](#msaa)
- [FXAA](#fxaa)
- [Subpixel Morphological AA](#subpixel-morphological-aa)
- [Temporal AA](#taa)
- [Super sampling](#super-sampling)

**Problem:** Big degradation of quality because of jagged lines. **Solution:** anti-aliasing or super sampling.
![](img/aa/noaa_taa.jpg)

### No AA

AA can be completely disabled. Currently, Forward Low render path has no AA enabled by default.

![](img/aa/noaa.jpg)

### MSAA

MSAA can be utilized for Forward Low render path, or any custom path that renders directly to framebuffer. MSAA can be enabled by setting **Render** - **Armory Build** - **Samples per Pixel**. Enter a value from 1 (disabled) to 16 (max quality).

### FXAA
The fastest technique, at a cost of blurring some elements. Used in Deferred Low path.
![](img/aa/fxaa.jpg)

### Subpixel Morphological AA
Used in Deferred path.
![](img/aa/smaa.jpg)

### Temporal AA
Used in Deferred High path. For dynamic scenes, velocity buffer is required for repojection.
![](img/aa/taa_smaa.jpg)

### Super-sampling
Very costly method producing very good results.
![](img/aa/taa_smaa_2x.jpg)

To enable super sampling, set screen scale in render nodes to 2.0. This effectively renders the scene at double the resolution.

<img src="img/aa/screenscale.png" alt="Drawing" style="width: 260px;"/>
