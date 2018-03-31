# Deploying to macOS

## Krom

- Create a new preset in `Armory Exporter` and select `MacOS (Krom)` target.
- Press `Publish`.
- That's it! Press `Triangle - Open Folder` to view exported files.

## Native (C++)

Create a new preset in *Properties - Render - Armory Exporter* and select MacOS target. Hit *Publish* to export XCode project files.

To proceed, install [XCode](https://developer.apple.com/xcode/). Once installed, open the project located at *blend_file_location/build_projectname/osx-build/projectname.xcodeproj*.

![](/platforms/img/macos/1.jpg)

Next, you can test, debug and profile your project in XCode.

![](/platforms/img/macos/2.jpg)

When you are ready to export final binary, press Menu - Product - Archive.
