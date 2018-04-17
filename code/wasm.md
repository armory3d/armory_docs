# WebAssembly

![](/code/img/wasm/0.jpg)

*Note: This feature requires Armory 0.4/git. Use [Armory Updater](http://armory3d.org/manual/#/dev/gitversion) to get it now.*

## Intro

[WebAssembly](http://webassembly.org/) (`Wasm`) is a binary instruction format for a stack-based virtual machine, designed as a portable target for compilation of languages like `C`/`C++`/`Rust`.

Armory can be programmed with `Wasm` for high-performance code execution. Including WebAssembly modules is supported on `HTML5` and `Desktop (Windows, Linux, macOS)` platforms using [Krom](https://github.com/Kode/Krom).

## Programming Armory in C

In the following example, we implement a trait (a piece of logic attached to an object) in `C`. This trait rotates a cube placed in the scene:

```c
#define WASM_EXPORT __attribute__((visibility("default")))

// Declare Armory API used in this module
// github.com/armory3d/armory/blob/master/Sources/armory/trait/internal/wasm_api.h
void notify_on_update(void* f);
int get_object(const char* name);
void set_transform(int object, float x, float y, float z,
	float rx, float ry, float rz, float sx, float sy, float sz);

WASM_EXPORT
void update() {
	static float rot = 0.0f;
	rot += 0.01f;
	set_transform(get_object("Cube"), 0, 0, 0, 0, 0, rot, 1, 1, 1); // Set cube rotation
}

WASM_EXPORT
int main() {
	notify_on_update(update); // Register callback
	return 0;
}
```

You can compile this `C` source into `Wasm` live at [webassembly.studio](https://webassembly.studio/?f=kl1f79ll4x). Place the resulting `.wasm` file into the `blend_location/Bundled` folder.

Select cube and navigate to `Properties - Object - Armory Traits`. Create a new `Wasm` trait and fill the `Module` property. Hit Play(`F5`) and watch the cube rotate!

<a href="./code/img/wasm/1.jpg">![](./code/img/wasm/1.jpg)</a>


- Example at [GitHub](https://github.com/armory3d/armory_examples/tree/master/web_assembly/c_trait)


## Call Wasm from Haxe

For even more flexibility, `wasm` can be called directly from a trait written in `Haxe`. Start with a simple `C` function:

```c
#define WASM_EXPORT __attribute__((visibility("default")))

WASM_EXPORT
float test() {
	return 0.01f;
}
```

You can compile this `C` source into `Wasm` live at [webassembly.studio](https://webassembly.studio/?f=gkkao6y44ga). Place the resulting `.wasm` file into the `blend_location/Bundled` folder.

To call `test()` from Haxe:

```haxe
package arm;
import iron.data.*

class MyTrait extends iron.Trait {
	public function new() {
		super();
		notifyOnInit(init);
	}

	function init() {
		Data.getBlob("main.wasm", function(b:kha.Blob) { // Load wasm blob
			var wasm = Wasm.instance(b); // Create wasm module
			var rot = 0.0;
			notifyOnUpdate(function() {
				rot += wasm.exports.test(); // Call function from wasm module!
				object.transform.setRotation(0, 0, rot);
			});
		});
	}
}

```

- Example at [GitHub](https://github.com/armory3d/armory_examples/tree/master/web_assembly/call_wasm)
