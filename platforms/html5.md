# Deploying to HTML5

## Browser

Create a new preset in *Properties - Render - Armory Exporter* and select HTML5 target. Hit *Publish* to export HTML5 files.

Resulting files will be located at *blend_file_location/build_projectname/html5*.

*Note that you need to copy these files to a web server or start a local server. Otherwise you will get a cross-origin error when opening index.html directly due to security reasons of web browsers. When playing HTML5 project from Blender, Armory starts a local server automatically. With Python installed, you can start the local server from terminal using `python -m SimpleHTTPServer` in build_projectname/html5 directory and then navigate to the http://localhost:8000 in your web browser.*

![](/platforms/img/html5/1.png)

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


## Resources

- [Example: Calling Haxe from JavaScript](https://github.com/armory3d/armory_examples/tree/master/call_hx)
- [Example: Calling JavaScript from Haxe](https://github.com/armory3d/armory_examples/tree/master/call_js)
- [Docs: Exposing Haxe classes for JavaScript](https://haxe.org/manual/target-javascript-expose.html)
- [Docs: Using Haxe classes in JavaScript](https://code.haxe.org/category/javascript/using-haxe-classes-in-javascript.html)
