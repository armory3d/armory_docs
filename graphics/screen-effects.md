# Screen Effects

This page provides an overview of the graphical screen effects that Armory can provide and visually enhance your projects and create immersion.

The full list of the various effects that is possible to use in Armory encompasses \(sorted alphabetically\):

* [Anti-aliasing](antialiasing.md) _\[Separate Article\]_
* [Auto Exposure](#auto-exposure) 
* [Bloom](#bloom)
* [Film Grain](#film-grain)
* [Fish-Eye](#fish-eye)
* [Global Illumination](global_illumination.md) _\[Separate Article\]_
* [Lens Flares](#lens-flares)
* [Lens Textures](#lens-textures)
* [Letterboxing](#letterboxing)
* [LUT Colorgrading](#lut-colorgrading)
* [Motion Blur](#motion-blur)
* [Screen-Space Raytraced Shadows](#ssrs)
* [Screen-Space Reflections](#ssr)
* [Sharpen](#sharpen)
* [Tonemapping](#tonemapping)
* [Vignette](#vignette)
* [Volumetric Fog](#volumetric-fog)
* [Volumetric Light](#volumetric-light)

_Please note that some of these effects have their own articles for further documentation._

---

## Auto Exposure

Auto Exposure or Eye Adaption is an effect where the the exposure in a scene is automatically adjusted based on the luminance in a frame. This effect mimics the ocular ability of the eye to adjust to various levels of darkness and light.

![](/graphics/img/se/auto_exposure.gif)

_Auto Exposure - Notice the shift in brightness when the scene average illumination is decreased._

##### Properties:

Auto Exposure Strength - _Adjusts the strength of the automatic exposure. Settings this value to 1 or more is not recommend, as plain white surfaces in full view becomes completely dark. \[Default: 0.7\]_

**How to:**

Toggle the boolean property located at: **Armory Render Path** &gt; **Auto Exposure**.

---

## Bloom

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

## Film Grain

Film Grain or Granularity is a screen effect typically seen in film and photography occurring due to small particles during the film processing. In Armory the effect is simulated by a shader adding noise each frame.

| Without grain | With grain |
| :--- | :--- |
| ![](/graphics/img/se/Without_Grain.gif) | ![](/graphics/img/se/With_Grain.gif) |

_A comparison of a scene with and without film grain._

##### Properties:

Strength - _Sets the strength of the film grain in the scene. \[Default: 2\]_

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Film Grain**.

## Fish Eye

In photography a fisheye lens is an ultra-wide lens used to create a lens distortion that allows for a camera to capture views larger than 100 degrees. In Armory the default distortion is set to a mild level, in order to get the slight view distortion found in games such as GTA V and Battlefield.

![](/graphics/img/se/fisheye.gif) 

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Fish Eye**.

## Lens Flares

Lens Flares is a photographic phenomenom where light is scattered inside the lens system of a camera. In Armory the lens flare effect is noticeable when a bright sun is placed in a scene.

![](/graphics/img/se/lens_flare.gif) 

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Lens Flare**.

## Lens Textures

Lens Textures in Armory is a texture overlayed on top of the screen to fit. This effect can, for instance, be used to simulate smudge and dust on a visor.

![](/graphics/img/se/lenstexture.gif)

##### Properties:

Lens Texture - Insert "luttexture.jpg" to make the engine look for the texture in the "Bundled" folder.

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Lens Texture**.

## Letterboxing

Letterboxing is an effect where a widescreen aspect ratio is transferred to a standard width video format. As the name refers to, the frame is compressed into a wider frame in the shape of a letterbox. In gaming it's often used during cutscenes and dialogues.

| Without letterboxing | With letterboxing |
| :--- | :--- |
| ![](/graphics/img/se/No_Letterbox.jpg) | ![](/graphics/img/se/Letterbox.jpg) |

##### Properties:

Size - The size in relation pf the width in relation to the letterboxing_. \[Default: 0.1\]_

## LUT Colorgrading

3D LUT based colorgrading is an effect where a user provided LUT file \(in Armory just a .jpg file\) adjusts the colors of the screen. Often used to create atmospheric scenes.

![](/graphics/img/se/render_result_noir.png)

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

## Motion Blur

Motion Blur is a method of replicating the apparent streaking of moving object usually occurring in photography when a camera either has long exposure or is undergoing rapid movement. In gaming, the effect is often used when the framerate is either low or deliberately capped, thus to improve the illusion of speed, motion blur is used as a postprocess effect. In Armory, there's two motion blur settings.

![](/graphics/img/se/motion_blur.gif)

_Notice the repetitive structures of the image as the camera is panned. The effect is distorted somewhat due to GIF image compression._

**Properties:**

Object Motion Blur - This option is the most taxing, but also the most precise as every object is motion blurred according to individual object's velocity, calculated by the position of the object in the previous frame.

Camera Motion Blur - This option blurs the entire frame according to the cameras movement direction. This is usually less taxing on the hardware, although more imprecise.

Intensity - This value controls the intensity of the effect.

## Screen-Space Raytraced Shadows

Screen-Space Raytraced Shadows (SSRS) is a very subtle shadowing effect that is added on detailed meshes. Usually it's needed when subtle yet sharp contact shadows are required.

![](/graphics/img/se/SSRS.gif)

**Properties:**

Step - This is the step size. It controls the scale of the shadowing, with smaller values meaning shadows on smaller scale objects, and larger values beginning to shadowing larger objects.

## Screen-Space Reflections

Screen-Space Reflection is a technique where screen-space objects is reflected on a glossy medium such as metal or water. The limitation of this shader is that only objects visible within the frame is reflected.

![](/graphics/img/se/screen-space-reflection.gif)

_Notice the reflections on the floor, reflecting the wall behind from the same frame space._

**Properties:**

Ray Step - The size of the ray steps. This value can be seen as an inverse resolution guide, lower values are more taxing but also provides better quality. At the same time, a too low distance might cause the ray step sizes to be too small, causing the objects further away to not get hit by rays, and not show up. To prevent this, adjusting the Ray Step Minimum can be used to counter this:

![](/graphics/img/se/SSRStep.gif)

Ray Step Minimum - Minimum size of the ray steps. Using this value along with the Ray Step can define a span in which the rays will search, in order to get objects both closer to and further away from reflective surface:

![](/graphics/img/se/SSRStepMin.gif)

Search Distance - Search distance of the rays, generally speaking - the higher the search distance is, the further the rays will search:

![](/graphics/img/se/SSRSearch.gif)

Falloff - The falloff is connected to the reflectivity of the material, and clamps out the reflectivity from rougher surfaces, essentially increasing the limit before rougher surfaces reflectivity.

![](/graphics/img/se/SSRFalloff.gif)

Jitter - This value jitters the reflected results from the rays, and can be used to increase the visual roughness of materials by jittering the received reflections.

![](/graphics/img/se/SSRJitter.gif)


**How to:**

Toggle the boolean property located at: **Armory Render Path** &gt; **SSR**.

## Sharpen

Tonemapping is a technique used in image processing and graphics used to map a set of colors to another in order to simulate the appearances of HDR images/frames to an SDR display set. Armory comes with 4 tonemapping algorithms:

![](/graphics/img/se/sharpen.gif)

_A comparison of how the different tonemapping operators affects the brightness and colors of a frame._

**How to:**

Select the tonemapping option located at: **Armory Render Props** &gt; **Sharpen**.



## Tonemapping

Tonemapping is a technique used in image processing and graphics used to map a set of colors to another in order to simulate the appearances of HDR images/frames to an SDR display set. Armory comes with 4 tonemapping algorithms:

* Filmic - The default option in Armory. 
* Filmic 2 - The ACES \(Academy Color Encoding System\) film mapping curve.
* Reinhard - A very commonly used tonemapping operator.
* Uncharted - An implementation of tonemapping developed for the game Uncharted 2.

| None | Filmic | Filmic2 | Reinhard | Uncharted |
| :--- | :--- | :--- | :--- | :--- |
| ![](/graphics/img/se/T_None.jpg) | ![](/graphics/img/se/T_Filmic.jpg) | ![](/graphics/img/se/T_Filmic2.jpg) | ![](/graphics/img/se/T_Reinhard.jpg) | ![](/graphics/img/se/T_Uncharted.jpg) |

_A comparison of how the different tonemapping operators affects the brightness and colors of a frame._

**How to:**

Select the tonemapping option located at: **Armory Render Props** &gt; **Tonemapping**.

## Vignette

Vignette is a screen-effect where the brightness is reduced at the periphery of a frame. It's often an unintended effect occurring in photography and optics due to lens limitations. In gaming, it's often used to create more focus on central points of the screen.

|  |
| :--- |
| _**Example showing vignette turned on and off...**_ |

![](/graphics/img/se/vignette.gif)

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Vignette**.

## Volumetric Fog

Volumetric Fog is an effect that is dependent on the depth of the scene. It allows to create foggy and misty scenes.

![](/graphics/img/se/volumetricFog.gif) 

**How to:**

Toggle the boolean property located at: **Armory Render Props** &gt; **Volumetric Fog**.

**Properties:**

Color - This adjusts the value of the volumetric fog.

A - The A value multiplier. This adjusts the strength of the fog based on the depth.

B - The B value multiplier. This is not implemented yet. Supposedly used in conjunction with value A to adjust the distance-based offset in the viewed direction.

## Volumetric Light

Volumetric Light \(often referred to as god rays\) is an effect where it allows the user to create beams of light emanating from a light source. In the real world, this effect is known as crepuscular rays and is present when strong light passes through a medium such as fog, gas, dust, etc. - In contrast to Volumetric Fog, this effect is dependent on the sun and it's orientation, with the effect being prominent along the cones of the main light.

![](/graphics/img/se/volumetricLight.gif) 

|  |
| :--- |
| _**Example showing volumetric lighting with the default settings.**_ |

![](/graphics/img/se/volumetricLight2.gif) 

|  |
| :--- |
| _**Example showing volumetric lighting with blue color, 5 turbidity and 100 steps.**_ |

**How to:**

Toggle the boolean property located at: **Armory Render Path** &gt; **Volumetric Light**.

Add a sunlight or a spotlight at the direction you want the volumetric light to be oriented.

**Properties:**

Turbidity - This value adjusts the strength of the haziness. A higher value indicates a stronger effect.

Steps - This value adjusts the quality of the haze. A higher value increases the quality, and makes the individual haze-rays harder to distinguish from one another. 

