# FAQ

[Display error output](#display-error-output)
[Unable to compile empty project](#unable-to-compile-empty-project)
[Player does not start](#player-does-not-start)
[Player runs slow](#player-runs-slow)
[HTML5 project not working locally](#html5-project-not-working-locally)
[Changes not reflected in Armory](#changes-not-reflected-in-armory)
[Multi-material meshes not rendered properly](#multi-material-meshes-not-rendered-properly)
[Mesh faces appear transparent](#mesh-faces-appear-transparent)
[Trouble persists](#trouble-persists)


## Display error output

On Windows, press **Window - Toggle System Console**. On Linux and Mac, Blender needs to be launched from console.



## Unable to compile empty project
Make sure SDK path is set up properly or that 'Bundled SDK' is enabled in add-on properties.
  
If you are on Windows, you may need to install [DirectX Setup](https://download.microsoft.com/download/1/7/1/1718CCC4-6315-4D8E-9543-8E28A4E18C4C/dxwebsetup.exe)
and [Visual C++ 2015 Redistributable x86](https://www.microsoft.com/en-us/download/details.aspx?id=48145).

In some cases there are reports of anti-virus deleting krafix shader compiler. Make sure no files are removed during SDK unpacking.



## Player does not start

### Clean project
Locate 'Armory Build' section in 'Render' panel and hit 'Clean' button. Try running your project again.

### Debug project in Kode Studio
Locate 'Armory Build' section in 'Render' panel and hit 'Kode Studio' button. This will load the project in a dedicated IDE. Hit F5 to run and observe console output for potential error reports.

### Select forward render path in camera data panel

### Make sure you can run [browser demos](http://armory3d.org/download.html)



## Player runs slow
### Lower graphics settings
By default, Armory uses a deferred render path. If you are running on older hardware, using a less demading forward path can help. Select active scene camera, locate 'Armory Props' in data panel, and choose 'forward_path' or 'forward_path_low' as render path.

### Run player in smaller area

### Set higher frame rate
Locate render panel - dimensions - frame rate option. Make sure to select 60 fps.



## HTML5 project not working locally
To run HTML5 files local server is required. Alternatively, launch project from Armory using the browser runtime. This will start local server automatically.



## Changes not reflected in Armory

In some cases the cache is kept even though the Blender data was modified. Cleaning the project will likely help. This will be fixed in the future.



## Multi-material meshes not rendered properly

Currently multi-material meshes may render wrong if materials are not coherent. Select object, enter Edit mode and hit **P - Split by Material**.



## Mesh faces appear transparent

Enable Backface Culling in 3D View - View - Properties - Shading to verify if there are culling issues.

In Blender, enter Edit mode, select all faces - press space - Make Normals Consistent. Alternatively, you might need to select the problematic faces individually - press space - Flip Normals.

To disable culling for material, select material - Armory Props - Advanced - Override Cull-Mode - None. To disable culling globally, check Force No Culling in World data - Armory Props - Flags. Fixing face normals is recommended as this will result in performance hit.



## Trouble persists
[Post a new forum topic, report an issue, or contact us directly!](http://armory3d.org/community.html)
