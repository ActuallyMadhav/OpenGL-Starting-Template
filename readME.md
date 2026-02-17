# OpenGL Project Template

A template project for OpenGL development with GLFW and Cocoa framework support on macOS.

## Overview

This is a reusable template for creating OpenGL applications on macOS. It's configured with:
- **GLFW 3.4** for window management and input handling
- **GLAD** for OpenGL function loading
- **OpenGL** for rendering
- **C++17** for modern C++ features
- **clang++** as the compiler

## Project Structure

```
opengl-test/
├── main.cpp                 # Main application code
├── glad.c                   # GLAD OpenGL loader implementation
├── readME.md               # This file (project documentation)
├── app                     # Compiled executable
├── app.dSYM/               # Debug symbols for debugging
├── .vscode/                # VS Code configuration and build tasks
└── dependencies/
    ├── include/
    │   ├── glad/           # GLAD header files
    │   └── GLFW/           # GLFW header files
    │       ├── glfw3.h
    │       └── glfw3native.h
    └── library/
        └── libglfw.3.4.dylib  # GLFW compiled library
```

## Prerequisites

- **macOS** (tested on Apple Silicon)
- **Xcode Command Line Tools** (includes clang++)
  ```bash
  xcode-select --install
  ```
- **GLFW 3.4** (included in `dependencies/`)
- **GLAD** (included in project - `glad.c`)

## Setup & Building

### Option 1: Using VS Code Tasks (Recommended)

1. Open the project in VS Code
2. Press `Cmd + Shift + B` to build or use the build task from the Command Palette

### Option 2: Manual Build

Compile from the terminal:

```bash
clang++ -std=c++17 -Wall -g \
  -I./dependencies/include \
  -L./dependencies/library \
  main.cpp glad.c \
  ./dependencies/library/libglfw.3.4.dylib \
  -o app \
  -framework OpenGL \
  -framework Cocoa \
  -framework IOKit \
  -framework CoreVideo \
  -framework CoreFoundation
```

## Running the Application

After building, run the executable:

```bash
./app
```

## Development Tips

- **Debugging**: The debug symbols are included in `app.dSYM/` for breakpoint debugging
- **Adding Files**: Create new `.cpp` files and update the build task to include them
- **GLAD**: The `glad.c` file is auto-generated and should not be modified directly
- **Includes**: Add custom header paths to the compiler flags in the build task
- **Libraries**: Add additional libraries using `-L` for library paths and `-l` for linking

## Using This as a Template

1. Copy this entire directory structure to a new project
2. Rename the folder to your project name
3. Modify `main.cpp` with your OpenGL code
4. Update this README with your project-specific information
5. Build and run as described above

## Troubleshooting

- **Build errors**: Ensure Xcode Command Line Tools are installed
- **GLFW not found**: Verify `dependencies/library/libglfw.3.4.dylib` exists
- **Framework errors**: Check that macOS frameworks are properly linked in build flags
- **Window issues**: GLFW on macOS requires proper Cocoa framework integration (already configured)

## Resources

- [YouTube Tutorial](https://www.youtube.com/watch?v=7-dL6a5_B3I&t=344s)
- [GLFW Documentation](https://www.glfw.org/documentation.html)
- [OpenGL Documentation](https://www.opengl.org/)
- [C++ Reference](https://en.cppreference.com/)
