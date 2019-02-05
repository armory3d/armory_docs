# Render Path

*This page is work in progress - most of the manual labor described here is to be automated.*

Armory is powered by a programmable render path system. This allows us to manage both forward & deferred renderers and easily extend it with additional passes while introducing the least possible overhead and reusing existing resources. The engine is also prepared for adding new renderers.

Render path is built when the game itself is being compiled. When a specific pass is disabled, it's completely gone to save resources.

## Extending compositor

If possible, perform additional post processing directly in compositor. This way everything is kept in a single pass. See [LUT-based-color-grading](https://github.com/armory3d/armory/commit/42b0aaadeda67b2eabde0344ebbb100f18bd8e0d). It is possible to access pre-tonemaped color, depth, normals,..

## Adding post-processing pass

For effects which do not fit into a single pass

- In [make_renderpath.py](https://github.com/armory3d/armory/blob/master/blender/arm/make_renderpath.py) - include additional shader files(`assets.add_shader_pass()`) and add defines(`assets.add_khafile_def()`)

- In [RenderPathForward.hx](https://github.com/armory3d/armory/blob/master/Sources/armory/renderpath/RenderPathForward.hx) / [RenderPathDeferred.hx](https://github.com/armory3d/armory/blob/master/Sources/armory/renderpath/RenderPathDeferred.hx) - load shaders (`path.loadShader()`), create render targets(`path.createRenderTarget()`) and add new commands

```haxe
#if rp_custom_pass
{
	// Draw into helper 'buf' render target
	path.setTarget("buf"); 
	// Bind current screen color
	path.bindTarget("tex");
	
	// Draw full-screen quad(actually triangle) using custom shader
	// file_name/shader_name/context_name
	path.drawShader("shader_datas/custom_pass/custom_pass");
	
	// NOTE: this step is temporary till the interface for adding custom passes improves
	// Copy results of custom_pass back to the "tex" render target,
	// which will then get picked up be compositor pass
	path.setTarget("tex");
	path.bindTarget("buf", "tex");
	path.drawShader("shader_datas/copy_pass/copy_pass");
}
#end
```

## Custom geometry pass

See [material_shaders](https://github.com/armory3d/armory_examples/tree/master/material_shaders) example.

- Create new [material definition](https://github.com/armory3d/armory_examples/blob/master/material_shaders/Bundled/MyMaterial/MyMaterial.json) in `blend_root/Bundled/your_material`
- In Blender, select material and set `Properties - Material - Armory Props - Custom Material` to `your_material`
- Create `your_material.vert.glsl` and `your_material.frag.glsl` shaders (.geom, .tesc, .tese are optional) in `blend_root/Shaders`

### Forward path

Minimal vertex shader:

```c
#version 450
in vec3 pos;
uniform mat4 WVP;
void main() {
	gl_Position = WVP * vec4(pos, 1.0);
}
```

Minimal fragment shader:

```c
#version 450
out vec4 fragColor;
void main() {
	fragColor = vec4(1.0);
}
```

### Deferred path

For deferred renderer, we need to encode fragment shader output into gbuffer layout.

Minimal vertex shader:

```c
#version 450
in vec3 pos;
in vec3 nor;
out vec3 wnormal;
uniform mat3 N;
uniform mat4 WVP;
void main() {
	wnormal = normalize(N * nor);
	gl_Position = WVP * vec4(pos, 1.0);
}
```

Minimal fragment shader:

```c
#version 450
#include "std/gbuffer.glsl"
in vec3 wnormal;
out vec4 fragColor[2];
void main() {
	// Pack normal into 2 components
	vec3 n = normalize(wnormal);
	n /= (abs(n.x) + abs(n.y) + abs(n.z));
	n.xy = n.z >= 0.0 ? n.xy : octahedronWrap(n.xy);
	// Define material values
	vec3 basecol = vec3(1.0);
	float roughness = 0.0;
	float metallic = 0.0;
	float occlusion = 1.0;
	float specular = 1.0;
	float materialId = 0.0
	// Store in gbuffer
	fragColor[0] = vec4(n.xy, packFloat(metallic, roughness), materialId);
	fragColor[1] = vec4(basecol.rgb, packFloat2(occlusion, specular));
}
```

See [voxel_world](https://github.com/armory3d/voxel_world) example.

## Writing custom render path

Create a new `blend_root/Sources/arm/renderpath/RenderPathCreator.hx` file. This will make Armory overwrite the internal render path with your own.

```haxe
package arm.renderpath;

class RenderPathCreator {

	public static function get():RenderPath {
		var path = new iron.RenderPath();
		path.commands = function() {
			path.setTarget(""); // Draw to framebuffer
			path.clearTarget(0xffffffff, 1.0); // Clear color & depth
			path.drawMeshes("mesh"); // Draw all visible meshes
		};
		return path;
	}
}
```

See [celshade](https://github.com/armory3d/driver_celshade_example) example.

It is also possible to replace/manipulate render path at runtime using the `iron.RenderPath.setActive(path)` command.
