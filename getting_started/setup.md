# Setup

Armory bundle comes with everything you need. **Blender 2.79** is used with **Armory player** built in. **Blender 2.8** builds are currently experimental. Armory sources are available at [GitHub](https://github.com/armory3d/).

- Unpack **Armory_version.zip** to your preferred location. *(On Windows, prefer a short path like 'C:\Dev' or unpack with [7-zip](http://www.7-zip.org) to prevent long path errors and speed-up the extraction.)*
- Run Blender located in the unpacked SDK. *(On Windows, you may need to enable it for the first time by clicking **More info** - **Run anyway**.)*

![](/getting_started/img/winrun.png)

- To verify everything is working correctly, save your .blend file, switch to `Cycles Render` or `Eevee` engine (using a drop down located in the info header) and hit **Play in Viewport** (P) button, located in the 3D view header.

![](/getting_started/img/setup2.jpg)

- Now you should be presented with an Armory rendered cube.

![](/getting_started/img/setup3.jpg)

- Continue to the Armory [tutorial](tutorial1.md) to learn more. If you have any trouble setting things up, [let us know](http://armory3d.org/community.html)!


## Using Armory as add-on

If you do not require the built-in player, Armory can be used as add-on only in standard Blender installation. The player will then launch in a separate window.

- [Download](http://armory3d.org/download.html) and unpack appropriate SDK for your platform.
- In Blender, Select **File** - **User Preferences...** and navigate to **Add-ons** tab.
- Click **Install from File...**
- Select **armory.py** located in *my_unpacked_sdk/Armory/armsdk/armory/blender/addon* (on MacOS the location is *my_unpacked_sdk/Armory/Blender.app/armsdk/armory/blender/addon*)
- **Enable** add-on and **set SDK location** to **my_unpacked_sdk/Armory/armsdk*
- Hit **Save User Settings** at the bottom and restart Blender. That's it!
