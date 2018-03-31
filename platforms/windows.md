# Deploying to Windows

## Krom

- Create a new preset in `Armory Exporter` and select `Windows (Krom)` target.
- Press `Publish`.
- That's it! Press `Triangle - Open Folder` to view exported files.

## Native (C++)

Create a new preset in *Properties - Render - Armory Exporter* and select Windows target. Hit *Publish* to export Visual Studio project files.

To proceed, install [Visual Studio](https://www.visualstudio.com/vs/community/). Make sure to install components for compiling C++ code. Once installed, open the project located at *blend_file_location/build_projectname/windows-build/project_name.sln*.

![](/platforms/img/windows/1.jpg)

Next, you can test, debug and profile your project in Visual Studio. When you are ready to export final binary, switch to Release mode and build the project.

![](/platforms/img/windows/2.jpg)

Once the build process finishes, copy the resulting binary from *Release* folder (in this case *untitled.exe*) -

![](/platforms/img/windows/3.jpg)

- to the *blend_file_location/build_projectname/windows* folder which also contains game assets.

![](/platforms/img/windows/4.jpg)

You can now package and distribute this folder!

## UWP (Universal Windows Platform)

TBD
