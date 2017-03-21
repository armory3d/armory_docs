# Using Git version

The process of using Git version of Armory in SDK is not yet automated but is quite straightforward. To proceed, git installation is required.

- Locate path where you unpacked Armory SDK and open *Armory/armsdk* on Windows and Linux, or Armory/blender.app/armsdk on MacOS
- Rename *iron* to *iron_backup* and *armory* to *armory_backup*
- Open a console/terminal in this location
- git clone https://github.com/armory3d/armory
- git clone https://github.com/armory3d/iron

Optionally, cloning Kha repository is recommended. Armory often takes advantage of latest Kha features, and when this happens, using older Kha revisions may produce build errors.

- Locate *Armory/armsdk/win32/Kha* (alternatively /linux64/Kha and /KodeStudio.app/Contents/Kha)
- Rename *Kha* to *Kha_backup*
- Open a console/terminal in this location
- git clone --recursive https://github.com/Kode/Kha
- cd Kha
- git submodule foreach --recursive git pull origin master
- git pull origin master

There is no need to recompile any libraries, you are now using the latest version of Armory. This may not be stable at all times - in case of issues, revert back to the *_backup* versions.

Going deeper:
- You may rebuild Krom: https://github.com/Kode/Krom
- You may rebuild Blender itself with integrated Krom: https://github.com/armory3d/blender_krom


Eventually, the plan is to provide a single command line script which will get all of this done automatically.
