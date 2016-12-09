# Using Git version

The process of using Git version of Armory in SDK is not yet automated but is quite straightforward. To proceed, git installation is required.

- Locate path where you unpacked Armory SDK and open *Armory/armsdk* on Windows and Linux, or Armory/blender.app/armsdk on MacOS
- Rename *iron* to *iron_backup* and *armory* to *armory_backup*
- Open a terminal in this location
- git clone https://github.com/armory3d/armory
- git clone https://github.com/armory3d/iron

There is no need to recompile any libraries, you are now using the latest version of Armory. This may not be stable at all times - in case of issues, revert back to the *_backup* versions.
