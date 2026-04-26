# Project README

## Overview
The project is a simple GUI application that captures video from the camera and encodes it. It supports Linux, Windows, Wine, and WebAssembly (Emscripten).

## Features
- Captures video from the camera.
- Encodes the captured frames into video format.
- Supports different operating systems: Linux, Windows, Wine, and WebAssembly.

## Project Structure
```
Gui_Camera_VideoEncoding/
├── build/              # .exe files produced by Main.c
├── src/                # Source code directory
│   ├── Main.c          # Entry point of the application
│   └── *.h             # Standalone header-based C-files, without *.c files that implement it
├── Makefile.linux      # Linux Build configuration
├── Makefile.windows    # Windows Build configuration
├── Makefile.wine       # Wine Build configuration for Linux cross-compile for windows
├── Makefile.web        # Emscripten Build configuration for WebAssembly
└── README.md           # This file
```

## Prerequisites
- C/C++ Compiler and Debugger (GCC, Clang)
- Make utility
- Standard development tools
- Libraries needed in specific projects:
  - Linux: X11, PNG, JPEG
  - Windows: WINAPI, User32, GDI32, Winmm
  - Wine: WINAPI, User32, GDI32, Winmm

## Build & Run
### Linux
To build and run on Linux:
```bash
cd Gui_Camera_VideoEncoding
make -f Makefile.linux all
make -f Makefile.linux exe
```

To clean the build artifacts:
```bash
make -f Makefile.linux clean
```

### Windows
To build and run on Windows:
```cmd
cd Gui_Camera_VideoEncoding
make -f Makefile.windows all
make -f Makefile.windows exe
```

To clean the build artifacts:
```cmd
make -f Makefile.windows clean
```

### Wine
To build and run using Wine on Linux:
```bash
cd Gui_Camera_VideoEncoding
make -f Makefile.wine all
WINEPREFIX=~/wine64 WINEARCH=win64 wine ./build/Main.exe
```

To clean the build artifacts:
```bash
make -f Makefile.wine clean
```

### WebAssembly (Emscripten)
To build and run for WebAssembly using Emscripten:
```bash
cd Gui_Camera_VideoEncoding
make -f Makefile.web all
emrun --no_browser --port 8080 ./build/index.html
```

To clean the build artifacts:
```bash
make -f Makefile.web clean
```

The project includes a single source file `Main.c` which handles the application logic, including capturing video from the camera and encoding it. The project is built using different Makefiles tailored for each target platform.