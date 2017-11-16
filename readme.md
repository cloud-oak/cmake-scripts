This repository contains CMake scripts for finding the `SDL2`, `SDL2_image`, `SDL2_ttf`, `PortAudio` libraries and headers.

## Usage

### General

In order to use these scripts, you first need to tell CMake where to find them, via
the `CMAKE_MODULE_PATH` variable. For example, if you put them in a
subdirectory called `cmake-scripts`, then in your root `CMakeLists.txt` add the line

```cmake
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${project_SOURCE_DIR}/cmake-scripts")
```

where `project` is the name of your project. You can then use the packages
themselves by adding

```cmake
find_package( SDL2 REQUIRED )

include_directories( ${SDL2_INCLUDE_DIR} )
target_link_libraries(target ${SDL2_LIBRARY} )

```

or whatever is appropriate for your project.

### mingw32 / msys

This section supplements ```Usage -> General``` section. You still are required
to incorporate ```General``` configuration settings in you CMakeLists.txt.

Because cmake binaries for windows aren't aware of *nix/win paths conversion,
default paths FindSDL2 will look in won't do any good. For that you should set SDL2_PATH variable.
For example:
```cmake
set(SDL2_PATH "D:\\apps\\SDL2\\i686-w64-mingw32")
```

```bash
mkdir build
cd build
cmake .. -G"MSYS Makefiles"
make
```


## Licence

I am not the original author of these scripts. I forked the SDL2 CMake scripts from @tcbrindle's repo and added other CMake Scripts I found useful. License information is provided in the header comment for each cmake-script.
All scripts are compatible with the 3-clause BSD licence.

## Bugs

These scripts are provided in the hope that you might find them useful. They
work for me and hopefully they'll work for you too. If you fix any
issues with them then I'd appreciate a pull request so other
users can get your fixes too, but that's up to you :-).


