# [Z]ig & [Ray]lib & Wa[sm]

## Overview

- Experimentation around Zig, Raylib and Wasm.
- A game in Zig using Raylib bindings and allowing plugins written in Wasm...
- Currently we are able to use Raylib and build a small WAT file.

## Installation

### Requirements
- To use *Zraysm* you will need [Raylib](https://github.com/raysan5/raylib) and [Wasmer](https://github.com/wasmerio/wasmer/releases).
  - For information we are testing with the following versions:
    - Raylib: Release v5.0
    - Wasmer: Release v4.3.2

### Install *Raylib* header and library
- You need to build [Raylib](https://github.com/raysan5/raylib)
- Create a directory called *raylib* (or modify *build.zig*)
- Then copy the `raylib.h`, `raymath.h` and `libraylib.a` into the *raylib/* directory
- As *Raylib* has a `build.zig` file it should be easy to build it with *Zraysm*

### Install *Wasmer* headers and library
- Download [Wasmer](https://github.com/wasmerio/wasmer/releases)
- Create a directory *wasmer*
- go into the directory and untar the previously downloaded release
  - we only need `lib/libwasmer.so` and the `include/*` but you can keep other stuff

- After installing *Raylib* and *Wasmer* you should have a tree like:
```
.
├── build.zig
├── LICENSE
├── raylib
│   ├── libraylib.a
│   ├── raylib.h
│   └── raymat.h
├── README.md
├── samples
│   ...
├── src
│   ...
├── wasmer
│   ├── include
│   │   ├── README.md
│   │   ├── wasmer.h
│   │   ├── wasmer_wasm.h
│   │   ├── wasm.h
│   │   └── wasm.hh
│   ├── lib
│   │   └── libwasmer.so
│   └── LICENSE
```

### Run *Zraysm*
- We have an issue using `libwasmer.a` so to run it:
  - `zig build && LD_LIBRARY_PATH=./wasmer/lib ./zig-out/bin/zraysm ./src/wat/gcd.wat`
  - or you can just do: `zig build run`
  - **Note**: only wasm function that takes two i32 arguments and returns one i32 can be called for now

## Changelog

**2024-06-24**  Gthvn1  <gthvn1@gmail.com>
  * Draw a ship

**2024-06-21**  Gthvn1  <gthvn1@gmail.com>
  * Read the WAT file as the first argument of `Zraysm`
  * Read a WAT file instead of using the string

**2024-06-20**  Gthvn1  <gthvn1@gmail.com>
  * Run a WAT string into our Zig code using Wasmer
    * It is the example in the *wasmer/include/README.md*

**2024-06-17**  Gthvn1  <gthvn1@gmail.com>
  * Add samples of wasmtime C API
    * don't know if we will use wasmtime or another runtime.

**2024-06-15**  Gthvn1  <gthvn1@gmail.com>
  * Add simple example of using WAT file into HTML
    * It runs outside of Zig
  * Link our program with Raylib
  * Calling a C function from Zig (see foo)
  * Initial commit

## Screenshots

### First ship...
<img align="center" src="https://github.com/gthvn1/zraysm/blob/master/screenshots/first_ship.png">
