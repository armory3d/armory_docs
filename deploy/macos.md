# Deploying to macOS

## Krom (JS)

- Create a new preset in `Armory Exporter` and select `macOS (Krom)` target.
- Press `Publish`.
- Press `Triangle - Open Folder` to view exported files.

## HashLink (C)

Create a new preset in `Properties - Render - Armory Exporter` and select `macOS (C)` target. Hit `Publish` to export XCode project files.

To proceed, install [XCode](https://developer.apple.com/xcode/). Once installed, open the project located at `blend_file_location/build_projectname/osx-hl-build/projectname.xcodeproj`.

Next, you can test, debug and profile your project in XCode.

When you are ready to export final binary, press `Menu - Product - Archive` in XCode.
