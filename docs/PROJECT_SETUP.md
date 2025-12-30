# Learning C - Project Setup

This document explains the project structure, build process, and debugging configuration.

## Project Structure

```
learning-c/
├── src/           # Source files (.c)
│   └── main.c
├── build/         # Build output (generated)
│   ├── *.o        # Object files
│   └── program    # Executable
├── docs/          # Documentation
├── .vscode/       # VS Code configuration
│   ├── launch.json
│   ├── tasks.json
│   └── settings.json
└── Makefile       # Build configuration
```

## Build Process

The project uses **Make** as the build system with **GCC** as the compiler.

### Makefile Overview

| Variable | Value | Description |
|----------|-------|-------------|
| `CC` | `gcc` | C compiler |
| `CFLAGS` | `-Wall -g` | Compiler flags (warnings + debug symbols) |
| `SRC_DIR` | `src` | Source directory |
| `BUILD_DIR` | `build` | Output directory |
| `TARGET` | `build/program` | Final executable |

### Compiler Flags

- `-Wall`: Enable all common warnings
- `-g`: Include debug symbols (required for debugging)

### Build Commands

**Build the project:**
```bash
make
```

**Build and run:**
```bash
make run
```

**Clean build artifacts:**
```bash
make clean
```

### How It Works

1. Make finds all `.c` files in `src/`
2. Each `.c` file is compiled to a `.o` object file in `build/`
3. Object files are linked together into the final `build/program` executable

## Debugging

The project is configured for debugging in VS Code using **LLDB** (the default debugger on macOS).

### Prerequisites

- **C/C++ Extension** for VS Code (Microsoft)
- **CodeLLDB** extension (optional, for enhanced LLDB support)

### Debug Configuration

The debug setup is defined in `.vscode/launch.json`:

| Setting | Value | Description |
|---------|-------|-------------|
| `name` | Debug C | Configuration name |
| `type` | cppdbg | C/C++ debugger |
| `program` | `build/program` | Executable to debug |
| `preLaunchTask` | build | Runs `make` before debugging |
| `MIMode` | lldb | Uses LLDB debugger |

### How to Debug

1. **Set a breakpoint**: Click in the gutter (left of line numbers) in your `.c` file
2. **Start debugging**: Press `F5` or go to Run > Start Debugging
3. The project will automatically build before launching the debugger

### Debug Controls

| Action | Shortcut |
|--------|----------|
| Continue | `F5` |
| Step Over | `F10` |
| Step Into | `F11` |
| Step Out | `Shift+F11` |
| Stop | `Shift+F5` |

### VS Code Tasks

Two build tasks are available (`.vscode/tasks.json`):

- **build** (default): Runs `make` to compile the project
- **clean**: Runs `make clean` to remove build artifacts

Run tasks via: Terminal > Run Task or `Cmd+Shift+B` (build)

## Quick Start

```bash
# Build the project
make

# Run the program
make run

# Or debug in VS Code with F5
```
