mesos-module-development
===

Docker image for use in compiling mesos modules for development using CMake.
Includes:
  - CMake (3.6.1)
  - GTest / GMock

The images include a `/src` volume which is expected to include the main `CMakeLists.txt` of the project;
mount your project root to this location.

The main entrypoint executes `cmake -DMESOS_VERSION:STRING={{mesos version matching image tag}}`.

Additional arguments can be passed to `cmake` by setting the `CMAKE_ARGS` environment variable.

Build output is placed in the `./build` directory by default; this can be overridden by setting
the `BUILD_DIR` environment variable.

Example
---

Assuming that
  - your project has a `CMakeLists.txt` at it's root
  - you're fine with output being placed in the `./build` folder
  - you want to build against Mesos version 1.0.1

then simply execute the following from the root of your project:

```
docker run --rm -it v $(pwd):/src mattdeboer/mesos-module-development:1.0.1
```
