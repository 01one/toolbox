# C++ Build Commands

## Basic C++ Compilation

### GCC for C Programs
```bash
gcc filename.c -o program_name
./program_name  # Linux/macOS
program_name.exe  # Windows
```

### G++ for C++ Programs
```bash
g++ filename.cpp -o program_name
./program_name  # Linux/macOS
program_name.exe  # Windows
```

### Default Output Filename
If you don't specify an output name with `-o`:
```bash
g++ script.cpp
./a.out  # Linux/macOS
a.exe  # Windows
```

## Compilation Options

Common compiler flags:
- `-g` - Enable debugging information
- `-Wall` - Enable most warning messages
- `-O` or `-O2` - Enable optimizations
- `-o <name>` - Specify output filename
- `-c` - Output an object file (.o) instead of an executable
- `-std=c++17` - Specify C++ standard (other options: c++11, c++14, c++20)
- `-std=c17` - Specify C standard (other options: c11, c99)

## Working with Include Directories

```bash
g++ -o program -I/path/to/include program.cpp
```

## Working with Libraries

### General Library Linking
```bash
g++ program.cpp -o program -L/path/to/libs -lname_of_library
```

### SDL2 Library Example

Generic SDL2 linking pattern:
```bash
gcc -std=c17 main.c -I/path/to/SDL2/include -L/path/to/SDL2/lib -Wall -lmingw32 -lSDL2main -lSDL2 -o main
```

Windows example with placeholder paths:
```bash
gcc -std=c17 main.c -I/SDL2/include -L/SDL2/lib -Wall -lmingw32 -lSDL2main -lSDL2 -o main
```

## Command Shortcuts

For Windows, you can combine compilation and execution:
```bash
gcc -o program program.cpp && program.exe
```

For Linux/macOS:
```bash
g++ -o program program.cpp && ./program
```

## Terminal Commands by Platform

### Linux/macOS
```bash
g++ -o hello hello.cpp
./hello
```

### Windows
```bash
g++ -o hello hello.cpp
.\hello.exe
```
