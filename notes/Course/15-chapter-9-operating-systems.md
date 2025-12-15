# Operating Systems: Managing, Coordinating, and Monitoring Resources

**DISCOVERING COMPUTERS 2018: Digital Technology, Data, and Devices - Module 9**

## Objectives Overview
1.  Explain the purpose of an operating system.
2.  Describe the start-up process and shutdown options on computers and mobile devices.
3.  Explain how an operating system provides a user interface, manages programs, manages memory, and coordinates tasks.
4.  Describe how an operating system enables users to configure devices, establish an Internet connection, and monitor performance.
5.  Identify file management and other tools included with an operating system.
6.  Explain how an operating system enables users to control a network or administer security.
7.  Summarize the features of several desktop operating systems.
8.  Briefly describe various server operating systems.
9.  Summarize the features and uses of several mobile operating systems.

## Evolution of Operating Systems
*   **1969**: Release of UNIX.
*   **1980s**: Personal Computer Proliferation.
*   **1990s**: Rise of the Internet.
*   **2000s**: Widespread Adoption of Virtualization Technology.
*   **2007+**: Mobile Computing Revolution.

### Construction of OS (Programming Languages)
*   **C/C++**: Used for the vast majority of OS kernels (Linux, Windows). Allows low-level operations and direct memory/hardware control.
*   **Rust**: Provides memory safety, preventing common errors like buffer overflows without sacrificing performance.
*   **Shell script**: Used for tools and automation scripts (boot up, file management), NOT the kernel.
*   **Assembly language**: Lowest-level language for critical parts like the "bootloader" or manipulating CPU instructions.
*   **Python**: Used for higher-level tasks (automation, data science), NOT the kernel.

## Operating System Functions
The **Operating System (OS)** is a set of programs that coordinate all the activities among computer or mobile device hardware.

### Key Functions
1.  **Start and shut down** computer/device.
2.  **Provide a user interface**.
3.  **Manage programs**.
4.  **Manage memory**.
5.  **Coordinate tasks**.
6.  **Configure devices**.
7.  **Monitor performance**.
8.  **Establish an Internet connection**.
9.  **File management** and updates.
10. **Control a network** and **Administer security**.

### Starting Computers
*   **BIOS (Basic Input/Output System)**: Firmware stored in ROM/Flash. Performs **POST (Power-On Self-Test)** to check hardware and allows settings.
*   **UEFI (Unified Extensible Firmware Interface)**: Modern replacement for BIOS.
*   **Boot Process**:
    1.  **POST**: Checks essential hardware (CPU, RAM, etc.).
    2.  **Locate OS**: Searches storage for the **bootloader**.
    3.  **Hand Over Control**: Bootloader loads the OS kernel into RAM.

### Power Options
*   **Sleep mode**: Saves open documents/programs to RAM, turns off unneeded functions, enters low-power state.
*   **Hibernate mode**: Saves open documents/programs to the internal hard drive, then removes power.

### User Interface (UI)
Controls how you enter data/instructions and how information is displayed.
*   **Graphical User Interface (GUI)**: Interact with menus and visual images (e.g., Windows, macOS).
*   **Command-Line Interface**: User types commands or presses special keys (e.g., Command Prompt, Terminal).
    *   **Shell**: The interface between the user and the OS kernel.
    *   **Common Shells**: `sh` (Bourne Shell), `bash` (Bourne Again Shell), `csh` (C Shell), `zsh` (Z Shell), Windows PowerShell.

### Virtual Machine (VM)
An environment on a computer in which you can install and run an operating system and programs.

### Managing Programs
*   **Single tasking** vs. **Multitasking**.
*   **Foreground** (active app) vs. **Background** (running but not in focus).
*   **Single user** vs. **Multiuser**.

## Memory Management
Optimizes the use of internal memory (RAM).
*   **RAM Types**:
    *   **SRAM (Static)**: Fast, expensive (Cache).
    *   **DRAM (Dynamic)**: Slower, cheap (Main memory).
*   **Virtual Memory**: A portion of a storage medium functioning as additional RAM. Uses **paging** and the **MMU (Memory Management Unit)** to translate virtual addresses to physical addresses.
*   **Fragmentation**:
    *   **External Fragmentation**: Storage wasted because available memory is divided into small, noncontiguous blocks. (Solution: Memory compaction, Paging).
    *   **Internal Fragmentation**: Allocated memory block is larger than requested, wasting space inside the block.

## Coordinating Tasks
*   The OS determines the order in which tasks are processed.
*   **Spooling**: Places documents to be printed in a buffer (queue) to increase efficiency.

## Configuring Devices
*   **Driver**: A small program that tells the OS how to communicate with a specific device.
*   **Plug and Play**: Automatically configures new devices upon connection.

## Monitoring Performance & Internet
*   **Performance Monitor**: Assesses and reports information about computer resources (e.g., Activity Monitor).
*   **Internet Connection**: OS provides tools to connect to Wi-Fi or wired networks.
    *   **PRL (Preferred Roaming List)**: Database in SIM cards indicating preferred networks.
    *   **UICC**: Smart card used in mobile terminals in GSM and UMTS networks.

## File Management & Tools
*   **File Manager**, Search, Image Viewer, Uninstaller, Disk Cleanup, Disk Defragmenter.
*   Screen Saver, File Compression, Backup and Restore, Power Management.

## Operating Systems Categories

### Multiuser / Server OS
Allows multiple users to share resources.
*   **Network Administrator**: Uses server OS to manage users and security.
*   **User Account**: Username/ID and Password.

### Desktop Operating Systems
Complete OS working on desktops/laptops.
*   **Windows**: Start menu, tiles, taskbar, widespread use.
*   **macOS**: Known for ease of use, Dock, UNIX-based.
*   **UNIX**: Multitasking OS from the 1970s.
*   **Linux**: Popular, multitasking, open-source, UNIX-based.
*   **Chrome OS**: Linux-based, designed for web apps.

### Mobile Operating Systems
Resides on firmware.
*   **Android**: Open source, Linux-based (Google).
*   **iOS**: Proprietary (Apple).
*   **Windows (Mobile Edition)**: Proprietary (Microsoft).

## Summary
*   Functions of operating systems.
*   Variety of desktop, server, and mobile operating systems.