# Using Git version

## Armory Updater

Navigate to `File - User Preferences... - Add-ons - Armory`. Before cloning, you may need to install Git first - hit `Install Git` button to open the download page. When installing on Windows, select `Use Git from the Windows Command Prompt` option.

Afterwards, select `Update SDK` and inspect the command line for details - the process should take just a few seconds. Once done, restart Blender for changes to take effect. If something goes wrong, use `Restore SDK` button to revert the changes.

![](/dev/img/gitversion/updater.png)

## Manual clone

- Install [Git](https://git-scm.com/download/win).
- Pick a location for cloning the sdk and open a terminal/command line here.

```
git clone --recursive https://github.com/armory3d/armsdk
cd armsdk
git submodule foreach --recursive git pull origin master
```

- In Blender, navigate to `File - User Preferences... - Add-ons - Armory`. Uncheck `Bundled SDK` and set path to the newly cloned `armsdk` folder.

#### Updating

```
cd armsdk
git submodule foreach --recursive git pull origin master
git pull origin master
```

---

### Going deeper:

- Build Krom: https://github.com/Kode/Krom
- Build Blender with integrated Krom: https://github.com/armory3d/blender_v8
