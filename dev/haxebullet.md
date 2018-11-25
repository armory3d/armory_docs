# HaxeBullet

## Bullet Physics
One of current Armory supported Physics Engine is through [Bullet Physics](https://pybullet.org/wordpress/) with [HaxeBullet](https://github.com/armory3d/haxebullet)

Please note, as at time of this written, HaxeBullet still does not support all of native C++ Bullet Physics implementation. Contribution is welcome!

Javascript backend for Krom/other Javascript deployments is based on [Ammo](https://github.com/kripken/ammo.js/).
Ammo supported Bullet API can be found in this [API Reference](https://github.com/kripken/ammo.js/blob/master/ammo.idl)

C++ backend for native C++ compile is based on [native Bullet Physics C++](https://github.com/bulletphysics/bullet3). Native implementation API docs can be found in this [API Reference](https://pybullet.org/Bullet/BulletFull/index.html)

For any HaxeBullet implementation, it is recommended to support APIs that are supported by both Ammo/native C++ Bullet codes to not run into different behavior on different platforms.

## Update HaxeBullet

- Install [Git](https://git-scm.com/download/win)
- Click the `Fork` button on [GitHub](https://github.com/armory3d/haxebullet)
- Pick a location, open a command line here and clone your forked repository
```
git clone https://github.com/my_username/haxebullet
```
- Apply your changes, then open a command line in your forked repository and push the changes
```
git add .
git commit -m "My haxebullet patch description"
git push origin master
```
- Create [pull request](https://github.com/armory3d/haxebullet/compare?expand=1) by clicking `compare across forks` and selecting your fork

- Thanks for contributing!

## Local Armory setup

When working on HaxeBullet patches, it is useful to setup the Armory3D locally and apply your modification in following folders:
```
/armsdk_path/armsdk/lib/haxebullet
```

Following is the Javascript backend implementation
```
/armsdk_path/armsdk/lib/js/ammo
```

Following is the C++ backend implementation
```
/armsdk_path/armsdk/lib/cpp/bullet
```

Following is the haxe API implementation
```
/armsdk_path/armsdk/lib/cpp/Sources/haxebullet/Bullet.hx
```

*Note [1]: Disable `Armory Project - Cache Compiler` to always recompile the project when you hit `Play`. There is no need to compile Armory itself, you will see the changes in action instantly.*

*Note [2]: If do not want to recompile every time, one can also use use the `Clean` button next to `Play` to manually clean up the project when needed* 

*Note [3]: It is especially important to clean up the project for any Javascripts/relate changes as the project will likely to cache these files, failure to do so may result changes not showing up*

## Example Update
For example, need to add support for following
```
BtWheelInfo.m_deltaRotation
```

Confirm both [native Bullet Physics C++](https://github.com/bulletphysics/bullet3). Native implementation API docs can be found in this [API Reference](https://pybullet.org/Bullet/BulletFull/index.html) and [API Reference](https://github.com/kripken/ammo.js/blob/master/ammo.idl)
 supported it
 
Update following in the Armory SDK
```
/armsdk_path/armsdk/lib/cpp/Sources/haxebullet/Bullet.hx
```

```
extern class BtWheelInfo {
	#if js
	public function new(ci:BtWheelInfoConstructionInfo):Void;
	public static inline function create(ci:BtWheelInfoConstructionInfo):BtWheelInfo {
		return new BtWheelInfo(ci);
	}
	#elseif cpp
	@:native("btWheelInfo")
	public static function create(ci:BtWheelInfoConstructionInfo):BtWheelInfo;
	#end

    ...
	public var m_deltaRotation:BtScalar;
	
	...
```

Test the change in vehicle template (with project cache clean at least once after the change)

The new change should show up

If there is problem like above API
```
/armsdk_path/armsdk/lib/cpp/Sources/haxebullet/Bullet.hx
```
returns null, it is likely the backend support is not ready

If there is problem with HaxeBullet implementation, it should error out at compile time with `api is not found` error