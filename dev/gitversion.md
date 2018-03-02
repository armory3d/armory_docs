# Using Git version

## Armory Updater

Navigate to `File - User Preferences... - Add-ons - Armory`. Before cloning, you may need to install Git first - hit `Install Git` button to open the download page. When installing on Windows, select `Use Git from the Windows Command Prompt` option.

Afterwards, select `Update SDK` and inspect the command line for details - the process should take just a few seconds. Once done, restart Blender for changes to take effect. If something goes wrong, use `Restore SDK` button to revert the changes.

![](/dev/img/gitversion/updater.jpg)

## Manual clone

### Windows
- Install [Git](https://git-scm.com/download/win)
- Locate path where you unpacked Armory SDK and open *Armory/armsdk*
- Rename *iron* to *iron_backup*, *armory* to *armory_backup* and *win32/Kha* to *win32/Kha_backup*
- Open a command line at *Armory/armsdk*

```
git clone https://github.com/armory3d/armory
git clone https://github.com/armory3d/iron
cd win32
git clone --recursive https://github.com/Kode/Kha
cd Kha
git submodule foreach --recursive git pull origin master
git pull origin master
```

#### Updating

- Open a command line at *Armory/armsdk*

```
cd iron
git pull
cd ../armory
git pull
cd ../win32/Kha
git submodule foreach --recursive git pull origin master
git pull origin master
```

### Linux
- Locate path where you unpacked Armory SDK and open *Armory/armsdk*
- Rename *iron* to *iron_backup*, *armory* to *armory_backup* and *linux64/Kha* to *linux64/Kha_backup*
- Open a terminal at *Armory/armsdk*

```
git clone https://github.com/armory3d/armory
git clone https://github.com/armory3d/iron
cd linux64
git clone --recursive https://github.com/Kode/Kha
cd Kha
git submodule foreach --recursive git pull origin master
git pull origin master
```

#### Updating

- Open a terminal at *Armory/armsdk*

```
cd iron
git pull
cd ../armory
git pull
cd ../linux64/Kha
git submodule foreach --recursive git pull origin master
git pull origin master
```

### MacOS

- Locate path where you unpacked Armory SDK and open *Armory/blender.app/armsdk*
- Rename *iron* to *iron_backup*, *armory* to *armory_backup* and *KodeStudio.app/Contents/Kha* to *KodeStudio.app/Contents/Kha_backup*
- Open a terminal at *Armory/blender.app/armsdk*

```
git clone https://github.com/armory3d/armory
git clone https://github.com/armory3d/iron
cd KodeStudio.app/Contents
git clone --recursive https://github.com/Kode/Kha
cd Kha
git submodule foreach --recursive git pull origin master
git pull origin master
```

#### Updating

- Open a terminal at *Armory/blender.app/armsdk*

```
cd iron
git pull
cd ../armory
git pull
cd ../KodeStudio.app/Contents/Kha
git submodule foreach --recursive git pull origin master
git pull origin master
```

---

You are now using the latest version of Armory. This may not be stable at all times - in case of issues, revert back to the *_backup* versions.

### Going deeper:

- Clone latest physics module into *armsdk/lib*: https://github.com/armory3d/haxebullet
- Clone latest ui module into *armsdk/lib*: https://github.com/armory3d/zui
- You may rebuild Krom: https://github.com/Kode/Krom
- You may rebuild Blender itself with integrated Krom: https://github.com/armory3d/krom_blender
