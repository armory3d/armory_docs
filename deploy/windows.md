# Deploying to Windows

## Krom (JS)

- Create a new preset in `Properties - Render - Armory Exporter` and select `Windows (Krom)` target.
- Press `Publish`.
- Press `Triangle - Open Folder` to view exported files.

<div style="width:75%">![](/deploy/img/windows/0.jpg)</div>

## HashLink (C)

Create a new preset in `Properties - Render - Armory Exporter` and select `Windows (C)` target. Hit `Publish` to export Visual Studio project files.

To proceed, install [Visual Studio](https://www.visualstudio.com/vs/community/). Make sure to install components for compiling C++ code. Once installed, open the project located at `blend_file_location/build_projectname/windows-hl-build/project_name.sln`.

<div style="width:75%">![](/deploy/img/windows/1.jpg)</div>

Next, you can test, debug and profile your project in Visual Studio. When you are ready to export final binary, switch to Release mode and build the project.

![](/deploy/img/windows/2.jpg)

Once the build process finishes, copy the resulting binary from `x64/Release` folder (in this case `untitled.exe`).

<div style="width:75%">![](/deploy/img/windows/3.jpg)</div>

To the `blend_file_location/build_projectname/windows-hl` folder which also contains game assets.

<div style="width:75%">![](/deploy/img/windows/4.jpg)</div>

You can now package and distribute this folder.
