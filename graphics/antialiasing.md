# Anti-aliasing (AA)

Aliasing has a big impact on the image quality. To fight it, Armory comes pre-equipped with several solutions. Each has varying quality / performance ratio.

- [No AA](#no-aa)
- [MSAA](#msaa)
- [FXAA](#fxaa)
- [Subpixel Morphological AA](#subpixel-morphological-aa)
- [Temporal AA](#taa)
- [Super sampling](#super-sampling)

![](/graphics/img/aa/noaa_taa.jpg)

### No AA

Disabled anti-aliasing.

![](/graphics/img/aa/noaa.jpg)

### MSAA

MSAA can be utilized for Forward render path, or any custom path that renders directly to framebuffer. MSAA can be enabled by setting **Armory Render Path** - **Renderer** - **MSAA**. Enter a value from 1 (disabled) to 16 (max quality).

### FXAA
The fastest technique, at a cost of blurring.
![](/graphics/img/aa/fxaa.jpg)

### Subpixel Morphological AA
More advanced technique producing less blur.
![](/graphics/img/aa/smaa.jpg)

### Temporal AA
For dynamic scenes, a velocity buffer is required for reprojection.
![](/graphics/img/aa/taa_smaa.jpg)

### Super-sampling
Costly method effectively rendering the scene at higher resolution.
![](/graphics/img/aa/taa_smaa_2x.jpg)
