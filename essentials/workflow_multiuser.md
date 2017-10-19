# Multi-User Workflow

This page discusses tools to help multiple people work on the same project.

## Linked Proxy
Project can be split into several individual `.blend` files. These `.blend` files are then combined into the main file using Blenders linking functionality. See bundled [example](https://github.com/armory3d/armory_examples/tree/master/linked_proxy).

## Proxy Tools
Once the objects are linked in the main file, locate helper tools in `Properties - Object - Armory Proxy`. In this panel you can turn full hierarchy of linked objects into proxies using the `Make Proxy` operator. You can also manage which properties to keep in sync with the original linked object. Checked properties are automatically synced at `.blend` load. You can also trigger the sync manually by pressing `ctrl + shift + o -> enter`.

## Editing linked data
Blender comes with a handy add-on which lets you jump straight into the source `.blend` of the selected linked object. Enable `Edit Linked Library` add-on to unlock this functionality. A video explaining how to use the add-on can be found [here](https://vimeo.com/41440647).

## Project Root
If you keep `.blend` files in sub-folders it's necessary to set the project root folder. Set `Properties - Render - Armory Project - Root` to the location of main `.blend` file. With project root correctly setup `.blend` files in sub-folders will be able to find the haxe traits, and it's also possible to `Play` the `.blend` files on their own.
