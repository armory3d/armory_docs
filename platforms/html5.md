# Deploying to HTML5

## Browser

Create a new preset in *Properties - Render - Armory Exporter* and select HTML5 target. Hit *Publish* to export HTML5 files.

Resulting files will be located at *blend_file_location/build_projectname/html5*.

*Note that you need to copy these files to a web server or start a local server. Otherwise you will get a cross-origin error when opening index.html directly due to security reasons of web browsers. When playing HTML5 project from Blender, Armory starts a local server automatically.*

![](/platforms/img/html5/1.png)

## Mobile browser

Compared to desktop, a limited set of WebGL extensions is exposed on mobile browsers. To account for this, select the `Mobile` preset in `Properties - Render - Armory Render Path - Preset`. `Mobile` preset is configured to run on every WebGL1 capable device.

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
    <p align="center"><canvas align="center" style="outline: none;" id='khanvas' width='1280' height='720'></canvas></p>
    <script src='kha.js'></script>
</body>
</html>
```
