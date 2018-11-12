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

AA can be completely disabled. Currently, Forward Low render path has no AA enabled by default.

![](/graphics/img/aa/noaa.jpg)

### MSAA

MSAA can be utilized for Forward Low render path, or any custom path that renders directly to framebuffer. MSAA can be enabled by setting **Render** - **Armory Build** - **Samples per Pixel**. Enter a value from 1 (disabled) to 16 (max quality).

### FXAA
The fastest technique, at a cost of blurring some elements. Used in Deferred Low path.
![](/graphics/img/aa/fxaa.jpg)

### Subpixel Morphological AA
Used in Deferred path.
![](/graphics/img/aa/smaa.jpg)

### Temporal AA
Used in Deferred High path. For dynamic scenes, a velocity buffer is required for reprojection.
![](/graphics/img/aa/taa_smaa.jpg)

### Super-sampling
Very costly method producing very good results.
![](/graphics/img/aa/taa_smaa_2x.jpg)
