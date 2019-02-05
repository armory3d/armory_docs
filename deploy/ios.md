# Deploying to iOS

Before running on mobile device, make sure the project is optimized to consume minimal resources. It is recommended to create a `Mobile` render path in `Properties - Render - Armory Render Path`. Additionally, simplifying materials, textures and geometry may be needed. To run on the lower than the maximum available resolution, set `Armory Render Path - Post Process - Resolution` property.

## HashLink (C)

Create a new preset in `Properties - Render - Armory Exporter` and select iOS (C) target. Hit `Publish` to generate iOS project files.

To proceed, install and run XCode from macOS App Store. Launch XCode by opening the generated project located at *blend_file_location/build_projectname/ios-hl-build/projectname.xcodeproj*. Connect your iOS device and press `Run`.

![](/deploy/img/ios/2.jpg)
