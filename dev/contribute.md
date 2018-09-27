# Contribute

## Creating a pull request

- Install [Git](https://git-scm.com/download/win)
- Click the `Fork` button on [GitHub](https://github.com/armory3d/armory)
- Pick a location, open a command line here and clone your forked repository
```
git clone https://github.com/my_username/armory
```
- Apply your changes, then open a command line in your forked repository and push the changes
```
git add .
git commit -m "My armory patch description"
git push origin master
```
- Create [pull request](https://github.com/armory3d/armory/compare?expand=1) by clicking `compare across forks` and selecting your fork

- Thanks for contributing!

## Local Armory setup

When working on Armory patches, it is useful to setup the SDK locally and apply your modification there.

*Note: Disable `Armory Project - Cache Compiler` to always recompile the project when you hit `Play`. There is no need to compile Armory itself, you will see the changes in action instantly.*

#### Armory

- Fork and clone the [armory repository](https://github.com/armory3d/armory) into `blend_location/Libraries/armory`, it will automatically get picked up for that project

#### Iron

- Fork and clone the [iron repository](https://github.com/armory3d/iron) into `blend_location/Libraries/iron`, it will automatically get picked up for that project

#### Full SDK

Alternatively, you can clone the whole SDK at once.

- Clone [armsdk](https://github.com/armory3d/armsdk) into `blend_location/armsdk`, it will automatically get picked up for that project - this lets you have a fully self-contained and portable project setup

- You can also point Armory to use the armsdk [at specific location](https://armory3d.org/manual/#/dev/gitversion?id=manual-clone)
