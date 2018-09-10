# Krom

[Krom](https://github.com/Kode/Krom) is the default runtime used to play Armory games. It is designed for fast compile times and performance, powered by the [Chakra](https://github.com/Microsoft/ChakraCore) or [V8](https://developers.google.com/v8/) engine. Compared to the pre-compiled environment (Armory can target C/C++ directly as well), Krom has several advantages.

When you clone Armory from git, there is no need to build anything. The engine is compiled alongside the game into `JS` instantly as you press the `Play` button. You can jump on the latest Armory version using the [built-in updater](https://armory3d.org/manual/#/dev/gitversion) anytime. You can tinker with engine sources and each modification is live instantly as you `Play`. Learn and experiment freely.

Krom exposes native hardware capabilities and runs on any graphics API. It is a single executable, which weights around 7.9MB/2.8MB(zip) on Windows/Chakra. Krom can run standalone or embedded in existing programs. Apart from JS, WebAssembly can be utilized to include C/C++ code.

A type safety is ensured at build-time, and stack trace is thrown for runtime errors. On top of that, debugger is available. Once ready to publish, Krom can deploy to Windows, Linux and macOS from a single platform in a matter of seconds. Deployed games can be updated just by patching the `krom.js` file. Krom also offers runtime scripting capabilities.
