# Transform

Transform describes the location, rotation, scale and dimensions of object. To access the transform in Haxe trait:

```haxe
var transform = object.transform;
```

To access transform properties in object-space:

```haxe
var m = transform.local; // Matrix
var l = transform.loc;   // Location
var r = transform.rot;   // Rotation
var s = transform.scale; // Scale
```

To access transform properties in world-space:

```haxe
var m = transform.world;                     // Matrix
var l = transform.world.getLoc();            // Location
var r = new Quat().fromMat(transform.world); // Rotation
var s = transform.world.getScale();          // Scale
```

To manipulate the transform:

```haxe
transform.translate(1, 2, 3); // x, y, z
transform.rotate(Vec4.zAxis(), 1.2); // Axis, angle in radians
```

Alternatively, modify the transform properties directly. To apply the changes, call `buildMatrix()`:

```haxe
transform.loc.set(0, 5, 0);
transform.scale.x = 2.0;
transform.buildMatrix();
```

To set location, rotation and scale using a matrix:

```haxe
var m = Mat4.identity();
transform.setMatrix(m);
```

To retrieve world-space up, right and look vectors:

```haxe
var up = transform.up();        // Z axis
var right = transform.right();  // X axis
var look = transform.look();    // Y axis
```

Example:
- https://github.com/armory3d/armory_examples/tree/master/script_transform
