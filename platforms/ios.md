# Contents

This section covers iOS specific topics.

# Building for iOS

Before running on mobile device, make sure the project is optimized to run smooth on your target hardware. It is recommended to select *Mobile* preset in  *Properties - Render - Armory Render Path*. Additionally, simplifying **materials, textures and geometry** may be needed. To run on the lower than the maximum available resolution, set *Armory Render Path - Resolution* property.

## Native (C++)

Create a new preset in *Properties - Render - Armory Exporter* and select iOS target. Hit *Publish* to generate iOS project files.

To proceed, install and run *XCode* from MacOS App Store. Launch XCode by opening the generated project located at *blend_file_location/build_projectname/ios-build/projectname.xcodeproj*. Connect your iOS device and press *Run*.

![](img/ios/2.jpg)

Once compiled, the project will launch on your device!
