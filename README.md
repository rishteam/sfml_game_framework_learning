# SFML game framework

SFML game framework case learning

## Build

* Dependency
  * C++14
  * SFML

```
mkdir build && cd build
cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=TRUE .. && make -j4
```

> `CMAKE_EXPORT_COMPILE_COMMANDS` option for generating `compile_commands.json` for setting up Sourcetrail project to trace code.

## Thanks

* [Hopson97/SFML-Game-Framework](https://github.com/Hopson97/SFML-Game-Framework)
