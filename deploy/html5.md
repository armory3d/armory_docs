# Deploying to HTML5

## Browser

Create a new preset in `Properties - Render - Armory Exporter` and select `HTML5 (JS)` target. Hit `Publish` to export HTML5 files.

Resulting files will be located at `blend_file_location/build_projectname/html5`.

*Note: To run the index.html you need to copy these files to a web server or start a local server. When playing HTML5 project from Blender, Armory starts a local server automatically.*

*Note: Armory will target webgl2 by default. If you require webgl1 support, enable `Legacy Shaders` option in Armory add-on preferences.* 

*Note: To further minimize export size, check [Optimize for size](https://armory3d.org/manual/#/essentials/optimize?id=optimize-for-size).* 

<div style="width:75%">![](/deploy/img/html5/0.jpg)</div>

## Mobile browser

Create a `Mobile` path in `Properties - Render - Armory Render Path`. Afterwards, assign the mobile path to the `Render Path` slot in the `Armory Exporter`.

*Note: Armory will target webgl2 by default. If you require webgl1 support, enable `Legacy Shaders` option in Armory add-on preferences.* 

## Embed

Embedding Armory projects into existing web pages is straightforward. Once the project is published, inspect exported `index.html` file. Take note of the `<canvas>` and `<script>` elements.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <title>Armory</title>
</head>
<body style="margin: 0; padding: 0;">
    <p align="center"><canvas align="center" style="outline: none;" id='khanvas' width='1280' height='720' tabindex='-1'></canvas></p>
    <script src='kha.js'></script>
</body>
</html>
```
