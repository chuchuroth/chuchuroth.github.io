---
layout: post
title:  "Raspberry Pi Platform and Python Programming module 2"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The Raspberry Pi necessitates the execution of an operating system, distinguishing it from platforms like the Arduino. The default operating system for Raspberry Pi is **Raspbian**, a Linux distribution. Proficiency in Linux is essential for effective use of the Raspberry Pi, including navigation, file management, and code execution.

### Linux Operating System Overview

*   **Core Concepts**: Much of the information regarding Linux commands and interfaces is applicable across various Linux distributions.
*   **Interfaces**: Linux offers both text-based and graphical user interfaces (GUI).
    *   **Text-Based Interface (Shell)**: A shell is a program that interprets user input and executes commands, serving as the text-based interface for the operating system. It provides **precise and complete control**, enabling all system operations, and is more convenient for remote use over a network due to lower data transmission requirements compared to a GUI. The default shell on Raspbian and most Linux systems is **Bash (Bourne Again SHell)**. Efficient shell usage requires memorizing basic commands.
    *   **Graphical User Interface (GUI)**: The GUI for Raspbian can be initiated by typing `startx` if the system does not boot directly to the desktop. This command starts the X Window System, which uses a window manager to determine the visual appearance of the GUI. Linux offers flexibility, allowing users to choose or create different window managers, unlike operating systems such as Windows or macOS, which have fixed GUI designs. Users can run both the GUI and a terminal simultaneously.
    *   **Terminal/Console**: A terminal or console is a text entry and display device that runs a shell. Modern use typically involves **virtual terminals**, which are windows on the screen where a shell operates. LXTerminal is the default terminal application in Raspbian, accessible from the GUI by clicking a screen icon in the top bar. In a terminal, commands are typed after a prompt (e.g., `$`) and executed upon pressing Enter.

### User Accounts and Permissions

*   **User Accounts**: Linux systems support multiple user accounts, each with a **username and password for identification and authentication**.
*   **Default Account**: On Raspberry Pi, the default username is `pi` with a default password of `raspberry`, which can be changed via `raspi-config`.
*   **Login Process**: The login process involves providing the username and password to access the system.
*   **Manual Pages (`man`)**: The `man` command provides access to manual pages (man pages), which are **local sources of information about Linux commands**, including their descriptions, synopses, and options. Users can type `man [command_name]` to view the manual page for a specific command.

### Filesystem Navigation and Operations

*   **Filesystem Structure**: An operating system provides a **filesystem**, which is a **hierarchy of directories (folders) and files**. The top-level directory in Linux is the **root directory**, denoted by a forward slash (`/`). Directories can contain other directories and files, forming a tree-like structure.
*   **Current Directory**: Each shell session has a **current directory**, where commands that reference file names without a full path will look for the specified file or directory.
*   **Filesystem Commands**:
    *   **`pwd` (Print Working Directory)**: Reports the absolute path of the current directory.
    *   **`cd` (Change Directory)**: Changes the current directory.
        *   `cd /path/to/directory`: Changes to a specified absolute path.
        *   `cd`: Changes to the default home directory of the current user account (e.g., `/home/pi` for the `pi` user).
        *   `cd ..`: Moves up one level in the directory hierarchy.
        *   `cd [directory_name]`: Moves down into a subdirectory relative to the current directory.
    *   **`ls` (List)**: Displays the contents (files and subdirectories) of the current directory.
        *   **`ls -l`**: Provides a **long listing format**, showing detailed information about each item, including permissions, owner, group, size, and modification date. The leftmost character in this output indicates if an item is a directory (`d`) or a file (`-`).
    *   **`mkdir` (Make Directory)**: Creates a new directory.
    *   **`rmdir` (Remove Directory)**: Deletes an empty directory. It will not remove a directory that contains files, serving as a safety precaution.

### File Creation and Viewing

*   **Creating Files**:
    *   **Programmatically**: Files can be created by code using functions like `Open` (in Python).
    *   **Manually (Text Editors)**: Text editors are used to manually create or view files containing plain text. Unlike word processors, text editors store only the typed characters and essential invisible characters (like carriage returns or tabs), without formatting information. Examples of text editors in Linux include VI, VIM, EMAX, and **Nano**.
    *   **Installing Nano**: Nano can be installed on Raspbian using the command `sudo apt-get install nano`.
    *   **Starting Nano**: To use Nano, type `nano` in a terminal window. Files can be saved and quit using control sequences.
*   **Viewing Files**:
    *   **Text Editor**: Opening a file with a text editor like Nano (e.g., `nano testfile`) displays its contents.
    *   **`cat` (Concatenate)**: Prints the entire contents of a file directly to the terminal (e.g., `cat testfile`).
    *   **`head`**: Displays the first ten lines of a file by default. The number of lines can be modified with options (e.g., `head -20`).
    *   **`tail`**: Displays the last ten lines of a file by default. Like `head`, the number of lines can be modified.

### File Manipulation Commands

*   **`cp` (Copy)**: Copies a file. It takes two arguments: the source file name and the destination (new file) name (e.g., `cp original_file new_file`).
*   **`mv` (Move)**: Used for both **renaming files** and **moving files to a different directory**.
    *   **Renaming**: `mv old_name new_name` changes the file's name.
    *   **Moving**: `mv file_name destination_directory`. If the second argument is an existing directory, the file is moved into that directory.

### File Permissions and Root Access

*   **File Ownership**: Every file in Linux has an **owner**, which is the user account that created the file.
*   **Access Permissions**: Files and directories have **access permissions** categorized as:
    *   **Read (r)**: Ability to view the contents of a file or list the contents of a directory.
    *   **Write (w)**: Ability to modify the file or create/delete files within a directory.
    *   **Execute (x)**: Ability to run the file (if it's a program) or access files/traverse into a directory.
*   **Permission Categories**: Permissions are assigned to three user groupings:
    *   **User**: Refers to the **file owner**.
    *   **Group**: Permissions for a defined group of users.
    *   **Other**: Permissions for all other users.
*   **Viewing Permissions**: Permissions are displayed in the leftmost column of the `ls -l` output, with a `d` for directories or a `-` for files, followed by nine characters representing read, write, and execute permissions for user, group, and others (e.g., `rwx r-x r-x`). A dash (`-`) indicates the absence of a permission.
*   **Root Account**: All Linux machines have a **root account**, which possesses the **highest permission level**, allowing access to all files and directories. Certain critical system files and directories are exclusively accessible (read, write, or at least write access) by the root account for safety, preventing accidental system damage by regular users.
*   **`sudo` (Switch User DO)**: A command used to **execute a single command with root permissions**. This is a safer alternative to continuously operating as root, as mistakes made while root can be destructive. Root permission is often required for tasks like installing programs, modifying, or updating the operating system, or installing drivers.

### Processes and System Control

*   **Processes**: A process is a **runtime instance of a program**. Operating systems like Linux enable **multiple processes to run concurrently** through rapid swapping, creating the illusion of simultaneous execution.
    *   **Foreground Process**: The process that the user is currently interacting with.
    *   **Background Processes (Demons)**: Processes that run in the background, performing essential tasks like email retrieval, file downloads, or virus checks without direct user interaction.
*   **Process Commands**:
    *   **`ps` (Process Status)**: Displays information about running processes.
        *   `ps`: Shows processes started from the current shell and user.
        *   `ps a`: Shows **all processes running on the machine**. Each process is identified by a unique **Process ID (PID)**.
    *   **`kill`**: Terminates a running process using its PID (e.g., `kill [PID]`). This is useful for stopping unresponsive applications.
*   **System Shutdown**:
    *   **`shutdown`**: Command used for **properly shutting down a Linux machine**. Unplugging a Linux machine without proper shutdown can corrupt data structures and files. The command executes necessary procedures like flushing buffers and closing files before powering down.
