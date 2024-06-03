# LC3 Virtual Machine

This repository hosts the implementation of a simplified virtual machine (VM) for the LC3 (Little Computer 3), a fictional computer used for educational purposes. This VM simulates the LC3's hardware environment, providing a platform to execute LC3 assembly code on a modern computer running Windows. This version is a modification of the code initially provided by [Justin Meiners and Ryan Pendleton](https://github.com/justinmeiners/lc3-vm).

## Features

- Full simulation of the LC3 instruction set
- Keyboard input handling without echo and line buffering
- Signal handling for graceful shutdown
- Big and little endian compatibility for memory operations

## Requirements

- Windows OS
- C++ Compiler with support for C99 (e.g., GCC, Clang)

## Installation

Clone the repository to your local machine:

```bash
git clone https://github.com/kidewi/lc3-vm.git
```

Compile the source code using any C99 compliant C compiler:

```bash
gcc -o lc3-vm vm.cpp
```

## Usage

To run a compiled LC3 program:

```bash
./lc3-vm [image-file1] ...
```

The VM expects at least one argument, which is the path to a binary image file containing LC3 machine code.

## Code Explanation

### Main Components

- **Register handling:** The VM includes a total of 10 registers used for various purposes (general purpose, program counter, and condition flags).
- **Memory management:** Simulates a 16-bit address space with a configurable maximum size.
- **Instruction set:** Implements the entire set of LC3 operations, including arithmetic, logic, and control instructions.

### Key Functions

#### `disable_input_buffering`

Disables input buffering and echo for the console, making keyboard interactions more responsive and suitable for VM operations.

```c++
void disable_input_buffering() {
    ...
}
```

#### `restore_input_buffering`

Restores the original console settings upon program termination or interrupt.

```c++
void restore_input_buffering() {
    ...
}
```

#### `read_image`

Reads a binary image file into the VM's memory, adjusting endianness as necessary.

```c++
int read_image(const char* image_path) {
    ...
}
```

#### `signal_handling`

Configures signal handling for graceful interruption and shutdown of the VM.

```c++
void handle_interrupt(int signal) {
    ...
}
```



