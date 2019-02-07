# Deploying to Android

Before running on mobile device, make sure the project is optimized to consume minimal resources. It is recommended to create a `Mobile` render path in `Properties - Render - Armory Render Path`. Additionally, simplifying materials, textures and geometry may be needed. To run on the lower than the maximum available resolution, set `Armory Render Path - Post Process - Resolution` property.

## HashLink (C)

Create a new preset in `Properties - Render - Armory Exporter` and select Android target. Hit `Publish` to generate android project files.

To proceed, install and run [Android Studio](https://developer.android.com/studio/index.html). Select `Open an existing Android Studio project`. The project is located at `blend_file_location/build_projectname/android-native-hl-build/projectname`.

![](/deploy/img/android/0.jpg)

Once the project is loaded, Android Studio will install required dependencies. Make sure to allow installing NDK. Afterwards, connect your device and press `Run`.

*Note: For command line builds, see [Build your app from the command line](https://developer.android.com/studio/build/building-cmdline)*

![](/deploy/img/android/1.jpg)
