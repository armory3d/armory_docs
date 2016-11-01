# Troubleshooting

## Unable to compile empty project
Make sure SDK path is set up properly or that 'Bundled SDK' is enabled in add-on properties.
  
If you are on Windows, you may need to install [DirectX Setup](https://download.microsoft.com/download/1/7/1/1718CCC4-6315-4D8E-9543-8E28A4E18C4C/dxwebsetup.exe)
and [Visual C++ 2015 Redistributable x86](https://www.microsoft.com/en-us/download/details.aspx?id=48145).

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

## Changes do not reflect in player

In some cases the cache is kept even though the Blender data was modified. Cleaning the project will likely help. This will be fixed in the future.

## Trouble persist
[Post a new forum topic, report an issue, or contact us directly!](http://armory3d.org/support.html)
