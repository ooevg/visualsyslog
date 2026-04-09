![](https://raw.githubusercontent.com/MaxBelkov/visualsyslog/master/screens/ico.png) Visual Syslog Server for Windows
===
Visual Syslog Server for Windows is a free open source program to receive and view syslog messages.
Useful when setting up routers and systems based on Unix/Linux.

Visual Syslog Server for Windows has a live messages view: switches to a new received message. Helpful color highlighting.
Useful message filtering. Customizable notification and actions.

[Read in Russian](readme_rus.md)

![Visual Syslog Server for Windows](https://github.com/MaxBelkov/visualsyslog/blob/master/screens/screen1.png?raw=true)

Features
===
* Receive messages from various devices via UDP or TCP protocol (compliant to RFC 3164)
* Syslog messages are displayed in real-time
* Stores messages in files on disk
* Log file rotation by size or by date
* Filter displayed syslog messages based on facility, priority, host, source address, tag or message contents
* Customizable color highlighting with nice 3D design
* Generating notifications depending on the content of the received message:
  * Show alarms windows
  * Play sound file
  * Send e-mail notifications via smtp server
  * Customizable notices format
* Performs actions depending on the content of the received message:
  * Run external program with params
  * Saving message to the specified file
* Support for sending mail via SMTP server with authentication SSL / TLS
  (Support Gmail and iCloud mail smtp servers. You can use the push notifications on your mobile device for instant delivery of alarms.)
* Lightweight and very fast
* Run as a Windows application
* Minimize to system tray
* Support Windows XP/Vista/7/8/8.1, Windows Server 2003/2008/2012
* Easy to install: adjustment is not required
* Import historical syslog messages after the start of the program
* View syslog messages from the file
* The ability to receive messages encoded in UTF8
* Free open source software, licensed under the GPL V2

Download
===
Visual Syslog Server for Windows download installer:  
[Last developper snapshot 1.6.4](https://github.com/MaxBelkov/visualsyslog/blob/master/Output/visualsyslog_setup.exe?raw=true)  
[Latest stable release 1.6.4](https://github.com/MaxBelkov/visualsyslog/releases/latest)

Installation
===
After installation Visual Syslog Server for Windows works immediately: adjustment is not required.
Waiting for messages on the UDP and TCP port 514 (default setting).
Visual Syslog Server is an Windows application (installing a system service is not required).
Installer adds firewall exception.

Building from sources
===

### Building on Windows (Native)

To build Visual Syslog Server for Windows from sources:

1. **Requirements:**
   - CodeGear RAD Studio C++Builder 2007 or compatible version
   - Indy.Sockets (VCL) version 10 components (http://www.indyproject.org/Sockets/index.EN.aspx)
   - Inno Setup Compiler 5.5.1(a) (optional, for building installer)

2. **Build steps:**
   - Open `visualsyslog.cbproj` in C++Builder
   - Build the project (Ctrl+F9 or Project → Build)
   - The executable will be created in the output directory

3. **Building installer (optional):**
   - Open `visualsyslog.iss` in Inno Setup Compiler
   - Compile the script to create the setup executable

### Building on Linux/Unix (Cross-compilation for Windows)

To cross-compile for Windows from Linux:

1. **Install MinGW-w64:**
   ```bash
   # Debian/Ubuntu
   sudo apt-get install mingw-w64
   
   # Fedora/RHEL
   sudo dnf install mingw-w64
   ```

2. **Install Qt for Windows (if using Qt-based build system):**
   - Download Qt for Windows MinGW from https://www.qt.io/download
   - Or use existing Qt installation with MinGW toolchain

3. **Configure and build:**
   ```bash
   # Create build directory
   mkdir build-win && cd build-win
   
   # Configure with CMake for Windows target
   cmake .. -DCMAKE_TOOLCHAIN_FILE=/path/to/mingw-toolchain.cmake \
            -DCMAKE_BUILD_TYPE=Release
   
   # Build
   cmake --build . --config Release
   ```

4. **Deploy:**
   - Copy required DLLs (Qt libraries, etc.) alongside the executable
   - Use `windeployqt` tool if using Qt:
     ```bash
     windeployqt visualsyslog.exe
     ```

**Note:** This project was originally developed for C++Builder. For cross-platform builds, you may need to adapt the build system (e.g., create CMakeLists.txt) and ensure compatibility with standard C++ libraries.

### Alternative: Using Docker

You can also build in a Docker container with pre-configured Windows toolchain:

```bash
docker run --rm -v $(pwd):/src -w /src mxeenv make
```

Support
===
Your questions and suggestions please send to ![](https://github.com/MaxBelkov/visualsyslog/blob/master/screens/m.png?raw=true)

Future plans
===
* Message statistics

If you need these or other functions let me know.  

Screenshots
===

Color highlighting setup

![Visual Syslog Server for Windows color highlighting](https://github.com/MaxBelkov/visualsyslog/blob/master/screens/screen2.png?raw=true)

Message processing setup

![Visual Syslog Server for Windows message processing](https://github.com/MaxBelkov/visualsyslog/blob/master/screens/screen3.png?raw=true)

Main setup

![Visual Syslog Server for Windows main setup](https://github.com/MaxBelkov/visualsyslog/blob/master/screens/screen6.png?raw=true)

Files rotation setup

![Visual Syslog Server for Windows files rotation setup](https://github.com/MaxBelkov/visualsyslog/blob/master/screens/screen5.png?raw=true)

Smtp server setup to send e-mail messages

![Visual Syslog Server for Windows smtp server setup](https://github.com/MaxBelkov/visualsyslog/blob/master/screens/screen4.png?raw=true)
