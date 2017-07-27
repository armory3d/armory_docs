# Contents

This section covers Windows specific topics.

# Building for Windows

## Native (C++)

Select *Windows* in *Properties - Render - Armory Project - Target*. Hit *Build* to generate Visual Studio project files.

![](img/windows/0.jpg)

To proceed, install [Visual Studio](https://www.visualstudio.com/vs/community/). Make sure to install components for compiling C++ code. Once installed, open the project located at *your_blend_file_location/build/windows-build/your_project_name.sln*.

![](img/windows/1.jpg)

Next, you can test, debug and profile your project in Visual Studio. When you are ready to export final binary, switch to Release mode and build the project.

![](img/windows/2.jpg)

Once the build process finishes, copy the resulting binary from *Release* folder (in this case *untitled.exe*) -

![](img/windows/3.jpg)

- to the *your_blend_file_location/build/windows* folder which also contains game assets.

![](img/windows/4.jpg)

You can now package and distribute this folder!

## UWP (Universal Windows Platform)

TBD

## Krom

TBD
