# Contents

This section covers iOS specific topics.

# Building for iOS

Before running on mobile device, make sure the project is optimized to run smooth on your target hardware. It is recommended to select *Forward Low* preset in  *Camera - Properties - Camera Data - Armory Render Path*. Additionally, simplifying **materials, textures and geometry** may be needed.

![](img/ios/0.jpg)

## Native (C++)

Select *iOS* in *Properties - Render - Armory Project - Target*. Hit *Build* to generate iOS project files.

![](img/ios/1.jpg)

To proceed, install and run *XCode* from MacOS App Store. Launch XCode by opening the generated project located at *your_blend_file_location/build/ios-build/your_project_name.xcodeproj*. Connect your iOS device and press *Run*.

![](img/ios/2.jpg)

Once compiled, the project will launch on your device!
