# Deploying to Linux

## Krom

- Create a new preset in `Armory Exporter` and select `Linux (Krom)` target.
- Press `Publish`.
- That's it! Press `Triangle - Open Folder` to view exported files.

## Native (C++)

For the C++ compilation to succeed you might need to install some additional packages - read more at [Kha/Wiki](https://github.com/Kode/Kha/wiki/Linux).

Create a new preset in *Properties - Render - Armory Exporter* and select Linux target. Hit *Publish* to export build files.

Afterwards, you can compile the project using the generated makefile in *blend_file_location/build_projectname/linux-build/Relesase* or using the [Code::Blocks](http://codeblocks.org) project located at *blend_file_location/build_projectname/linux-build*.

In order for the resources to load correctly you will need to copy the contents of *blend_file_location/build_projectname/linux* into where the compiled executable file *projectname* is located.

If built using the makefile running `cp -a build_projectname/linux/. build_projectname/linux-build/Release/` where your Blender file is will do this.

You can now package and run your game!
