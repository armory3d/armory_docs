# Screen Effects

This page provides an overview of the graphical screen effects that Armory can provide and visually enhance your projects and create immersion.

The full list of the various effects that is possible to use in Armory encompasses \(sorted alphabetically\):

* [Anti-aliasing](/graphics/antialiasing.md) _\[Separate Article\]_
* [Auto Exposure](#auto-exposure) 
* [Bloom](#bloom)
* [Film Grain](#film-grain)
* [Fish-Eye](#fish-eye) _\[To be written...\]_
* [Global Illumination](/graphics/global_illumination.md) _\[Separate Article\]_
* [Lens Flares](#lens-flares) \[_To be written..._\]
* [Lens Textures](#lens-textures)
* [Letterboxing](#letterboxing)
* [LUT Colorgrading](#lut-colorgrading)
* [Motion Blur](#motion-blur)
* [Screen-Space Raytraced Shadows](#ssrs)
* [Screen-Space Reflections](#ssr)
* [Tonemapping](#tonemapping)
* [Vignette](#vignette)
* [Volumetric Fog](#volumetric-fog) _\[To be written...\]_
* [Volumetric Light](#volumetric-light)

_Please note that some of these effects have their own articles for further documentation._

---

## Auto Exposure {#auto-exposure}

Auto Exposure or Eye Adaption is an effect where the the exposure in a scene is automatically adjusted based on the luminance in a frame. This effect mimics the ocular ability of the eye to adjust to various levels of darkness and light.

|  |
| :--- |
| _**To do: .....Insert an illustratory gif here...**_ |

##### Properties:

Auto Exposure Strength - _Adjusts the strength of the automatic exposure. Settings this value to 1 or more is not recommend, as plain white surfaces in full view becomes completely dark. \[Default: 0.7\]_

**How to:**

Toggle the boolean property located at: **Armory Render Path** &gt; **Auto Exposure**.

## Bloom {#bloom}

Bloom or Glow is a screen-effect that reproduces artifacts occurring in real world cameras, and helps giving the illusion of bright light seen through a camera. Due to the limitations of typical display sets not supporting HDR \(High Dynamic Range\), the possibility to render exceptionally bright objects is not available and thus clamped to an ordinary white color on SDR \(Standard Dynamic Range\). Despite this, game engines can still take HDR into account in terms of effects, where the HDR values are made available for shaders, with bloom being one of them.

With the default settings Armory Engine adds bloom for elements that have a brightness higher than what an SDR display set is capable of rendering \(A value of 1 being equal to white\).  
![](/graphics/img/se/Bloom_Image.jpg)

_Bloom used in a scene. Note the glow surrounding the bright areas._

##### Properties:

Threshold - _Sets the delimiting threshold for when the bloom effect is applied. Lower values applies the bloom effect to less bright elements. \[Default: 1\]_

Strength - _Adjusts the strength of the bloom effect \[Default: 3.5\]_

Radius - _Adjusts the radius of the bloom. Higher values increases the size of the glow. \[Default: 3\]_

**How to:**

Toggle the boolean property located at: **Armory Render Path** &gt; **Bloom**.

| Blend example |
| :--- |
| [https://github.com/armory3d/armory\_examples/tree/master/render\_bloom](https://github.com/armory3d/armory_examples/tree/master/render_bloom) |

## Film Grain {#film-grain}

Film Grain or Granularity is a screen effect typically seen in film and photography occurring due to small particles during the film processing. In Armory the effect is simulated by a shader adding noise each frame.

| Without grain | With grain |
| :--- | :--- |
| ![](/graphics/img/se/Without_Grain.gif) | ![](/graphics/img/se/With_Grain.gif) |

_A comparison of a scene with and without film grain. _

##### Properties:

Strength - _Sets the strength of the film grain in the scene. \[Default: 2\]_

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Film Grain**.

## Fish Eye {#fish-eye}

To be written...

## Lens Flares {#lens-flares}

To be written...

## Lens Textures {#lens-textures}

To be written...

## Letterboxing {#letterboxing}

Letterboxing is an effect where a widescreen aspect ratio is transferred to a standard width video format. As the name refers to, the frame is compressed into a wider frame in the shape of a letterbox. In gaming it's often used during cutscenes and dialogues.

| Without letterboxing | With letterboxing |
| :--- | :--- |
| ![](/graphics/img/se/No_Letterbox.jpg) | ![](/graphics/img/se/Letterbox.jpg) |

##### Properties:

Size - The size in relation pf the width in relation to the letterboxing_. \[Default: 0.1\]_

| Blend Example |
| :--- |
| Going to be done... |

## LUT Colorgrading {#lut-colorgrading}

3D LUT based colorgrading is an effect where a user provided LUT file \(in Armory just a .jpg file\) adjusts the colors of the screen. Often used to create atmospheric scenes.![](/graphics/img/se/Render Result - Noir.png)

_A scene showing an example of a Noir/BW LUT file._

**How to:**

In your project folder, make a folder called "Bundled" and in that folder, provide a 512x512 LUT called "luttexture.jpg".

In Armory Render Props &gt; LUT Texture, write "luttexture.jpg".

**How to make your own LUT files \(recommended procedure\):**

First, take a screenshot of your scene that you haven't colorgraded yet, and open it in your favorite image editor \(Photoshop, Affinity Photo, Gimp, etc.\)

In the corner, put this a color neutral LUT file \(included in the blend example below\) alongside and begin adding adjustments.

Delete your screenshot, so only the 512x512 is visible with your LUT and your color adjustments.

Save it as "luttexture.jpg" using the adjustments you've made.

| Blend Example |
| :--- |
| [https://github.com/armory3d/armory\_examples/tree/master/render\_lut\_colorgrading](https://github.com/armory3d/armory_examples/tree/master/render_lut_colorgrading) |

## Motion Blur {#motion-blur}

To be written...

## Screen-Space Raytraced Shadows {#ssrs}

To be written...

## Screen-Space Reflections {#ssr}

Screen-Space Reflection is a technique where screen-space objects is reflected on a glossy medium such as metal or water. The limitation of this shader is that only objects visible within the frame is reflected.

**Properties:**

Ray Step - _A placeholder description..._

Ray Step Minimum - _A placeholder description..._

Search Distance - _A placeholder description..._

Falloff - _A placeholder description..._

Jitter - _A placeholder description..._

**How to:**

Toggle the boolean property located at: **Armory Render Path** &gt; **SSR**.

## Tonemapping {#tonemapping}

Tonemapping is a technique used in image processing and graphics used to map a set of colors to another in order to simulate the appearances of HDR images/frames to an SDR display set. Armory comes with 4 tonemapping algorithms:

* Filmic - The default option in Armory. 
* Filmic 2 - Default option in Unreal Engine. Uses the ACES \(Academy Color Encoding System\) film mapping curve.
* Reinhard - A very commonly used tonemapping operator.
* Uncharted - An implementation of tonemapping developed for the game Uncharted 2.

| None | Filmic | Filmic2 | Reinhard | Uncharted |
| :--- | :--- | :--- | :--- | :--- |
| ![](/graphics/img/se/T_None.jpg) | ![](/graphics/img/se/T_Filmic.jpg) | ![](/graphics/img/se/T_Filmic2.jpg) | ![](/graphics/img/se/T_Reinhard.jpg) | ![](/graphics/img/se/T_Uncharted.jpg) |

_A comparison of how the different tonemapping operators affects the brightness and colors of a frame._

**How to:**

Select the tonemapping option located at: **Armory Render Props** &gt; **Tonemapping**.

## Vignette {#vignette}

Vignette is a screen-effect where the brightness is reduced at the periphery of a frame. It's often an unintended effect occurring in photography and optics due to lens limitations. In gaming, it's often used to create more focus on central points of the screen.

|  |
| :--- |
| _**To do: .....Insert an illustratory jpg's here...**_ |

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Vignette**.

## Volumetric Fog {#volumetric-fog}

To be written...

## Volumetric Light {#volumetric-light}

Volumetric Light \(often referred to as god rays\) is an effect where it allows the user to create beams of light emanating from a light source. In the real world, this effect is known as crepuscular rays and is present when strong light passes through a medium such as fog, gas, dust, etc.

| No volumetric light | With volumetric light |
| :--- | :--- |
| ![](/graphics/img/se/No_Volumetric_Lights.jpg) | ![](/graphics/img/se/Volumetric_Lights.jpg) |

_A scene with an without volumetric light turned on. The light beams coming through the windows are visible on the right. Also note that the volumetric light affects the global illumination._

**How to:**

Toggle the boolean property located at: **Armory Render Path** &gt; **Volumetric Light**.

Add a spotlight pointing to where you want volumetric light to be.

