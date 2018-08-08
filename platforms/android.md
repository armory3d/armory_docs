# Deploying to Android

Before running on mobile device, make sure the project is optimized to run smooth on your target hardware. It is recommended to select *Mobile* preset in  *Properties - Render - Armory Render Path*. Additionally, simplifying **materials, textures and geometry** may be needed. To run on the lower than the maximum available resolution, set *Armory Render Path - Resolution* property.

## Native (C++)

Create a new preset in *Properties - Render - Armory Exporter* and select Android target. Hit *Publish* to generate android project files.

To proceed, install and run [Android Studio](https://developer.android.com/studio/index.html). Select *Open an existing Android Studio project*. The project is located at *blend_file_location/build_projectname/android-native-build/projectname*.

![](/platforms/img/android/2.jpg)

Once the project is loaded, make sure to install *NDK* by opening up *SDK Manager - SDK Tools* from Android Studio.

![](/platforms/img/android/3.jpg)

Android Studio may ask you to install additional tools. Continue till you resolve all dependencies. To speed up the build process, select 'armv7' target from the Build Variants tab. **Connect your device** and press *Run*. Build process can take up to several minutes when compiling for the first time.

Note: If you experience build errors, make sure the 'armv7' build variant is selected.

Note: For command line builds, see [Build your app from the command line](https://developer.android.com/studio/build/building-cmdline)

![](/platforms/img/android/4.jpg)

Once compiled, the project will launch on your device!

## Krom

TBD
