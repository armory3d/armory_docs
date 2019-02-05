# Setup

Armory bundle comes with everything you need.

- [Download SDK](http://armory3d.org/download.html).
- Unpack `Armory_version.zip` to your preferred location. *(On Windows, prefer a short path like `C:\Dev` or unpack with [7-zip](http://www.7-zip.org) to prevent long path errors and speed-up the extraction.)*
- Run Blender located in the unpacked SDK. *(On Windows, you may need to enable it for the first time by clicking **More info** - **Run anyway**. On Linux, open terminal in the extracted folder and type `./blender`. On macOS, see `instructions.txt` file.)*
---
- To verify everything is working correctly, save your .blend file and hit `Play` (F5) button, located in the `Properties - Render - Armory Player` panel.
- Continue to the [Playground tutorial](/getting_started/playground.md) to learn more.

## Troubleshooting

- For old graphics cards, create a `Mobile` path in `Properties - Render - Armory Render Path`.
- When naming folders/files, prefer unaccented alphabetical letters `A-Z`.
- If you wish to isolate config for the bundled Blender, create empty `config` folder in `Armory/2.80`.
- If you have any trouble setting things up, [let us know](http://armory3d.org/community.html)!

### Windows

- To see error messages, start Blender from console or press `Blender - Window - Toggle System Console`.
- `Type not found : Main` error - save your .blend in a safe path like `C:\Users\user_name\Documents\test`, otherwise Windows may prevent writing the files.
- If you get missing .dll errors, try installing [Visual C++ Redistributable for Visual Studio 2017](https://go.microsoft.com/fwlink/?LinkId=746572).

### Linux

- To see error messages, start Blender from terminal using `./blender`.

### macOS

- To see error messages, start Blender from terminal using `/path/to/Armory/blender.app/Contents/MacOS/blender`.
- Due to security elements of macOS, you may get a `file corrupted` error. Try starting Blender from terminal like described above.


## Using Armory as add-on

Armory can be used as a standard add-on in existing Blender installation.

- [Download](http://armory3d.org/download.html) and unpack appropriate SDK for your platform.
- In Blender, Select `Edit - Preferences...` and navigate to the `Add-ons` tab.
- Click `Install...`.
- Select `armory.py` located in `my_unpacked_sdk/Armory/armsdk/armory/blender/addon` (on MacOS the location is `my_unpacked_sdk/Armory/Blender.app/armsdk/armory/blender/addon`).
- **Enable** Armory add-on.
- Set `SDK Path` property to `my_unpacked_sdk/Armory/armsdk`.
- Hit `Save Preferences` and restart Blender.
