# Simple demo of simdjson as a CMake dependency using ExternalProject_Add
[![Ubuntu](https://github.com/simdjson/cmakedemo_externalproject/actions/workflows/ubuntu.yml/badge.svg)](https://github.com/simdjson/cmakedemo_externalproject/actions/workflows/ubuntu.yml)

This repository is meant to serve as an example of how to use [simdjson](https://github.com/simdjson/simdjson) as a `CMake` dependency using `ExternalProject_Add`. It requires CMake 3.16 or better. Though it should work under Linux if you have an up-to-date system, it is untested under different platforms such as Visual Studio.

Usage:

```
cmake -B build && cmake --build build -v && ./build/src/test
```

The simple `CMake` project builds a simple parser (`./src/test`) which can parse a given JSON document (provided as a command-line parameter) and determine whether it is valid JSON.


A simpler approach is to use simdjson as Git submodule, or just as subdirectory. See [cmakedemo](https://github.com/simdjson/cmakedemo).

Please refer to the main [simdjson](https://github.com/simdjson/simdjson) project for further documentation.


## FetchContent

We can also do [a demo using a single CMakeLists.txt file](https://github.com/simdjson/cmake_demo_single_file).
