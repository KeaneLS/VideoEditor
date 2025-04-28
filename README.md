# Video Editor

A Qt-based video editing application.

## Project Structure

```
.
├── build/          # Build directory (generated files)
│   ├── bin/       # Compiled executables
│   └── lib/       # Compiled libraries
├── deploy/        # Deployment directory (runtime files)
├── src/           # Source code
│   └── main.cpp   # Main application file
└── CMakeLists.txt # Build configuration
```

## Prerequisites

- CMake 3.16 or higher
- Qt6
- C++17 compatible compiler

## Building the Project

1. Create a build directory:
```bash
mkdir build
cd build
```

2. Configure the project:
```bash
cmake ..
```

3. Build the project:
```bash
cmake --build .
```

The compiled executable will be available in `build/bin/`.

## Running the Application

After building, you can run the application from the `build/bin` directory:

```bash
./VideoEditor
```

## Development

- Source code is located in the `src` directory
- Build artifacts are generated in the `build` directory
- Runtime files are placed in the `deploy` directory 