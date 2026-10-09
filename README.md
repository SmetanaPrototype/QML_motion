# Simple Function (Qt/QML)

A small Qt/QML desktop application built with CMake. It plots a sine function using `Canvas` — a minimal example of integrating C++ and QML via Qt 6.

## Tech Stack

- **C++** — application entry point
- **Qt 6 / QML** — UI and rendering
- **CMake** — build system
- **GitHub Actions** — automated builds for Windows and Linux


## Dependencies

### Windows

1. **Qt 6.4 or newer** — download from [qt.io/download](https://www.qt.io/download-qt-installer).
   During installation, select:
   - Qt 6.8.x → **MSVC 2022 64-bit**
   - **Qt Quick / QtDeclarative** module

2. **CMake 3.16+** — [cmake.org/download](https://cmake.org/download/).
   During installation, enable **Add CMake to the system PATH**.

3. **Visual Studio 2022** (Community is enough) with **Desktop development with C++** workload — [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/community/).

4. **Git** — [git-scm.com](https://git-scm.com/download/win).

After installing Qt, add its `bin` folder to `PATH` or set `CMAKE_PREFIX_PATH` when configuring:

```powershell
$env:CMAKE_PREFIX_PATH = "C:\Qt\6.8.2\msvc2022_64"
```

### Linux (Ubuntu / Debian)

Install Qt 6, QML modules, and build tools in one command:

```bash
sudo apt update
sudo apt install -y \
  build-essential \
  cmake \
  git \
  qt6-base-dev \
  qt6-declarative-dev \
  qt6-tools-dev \
  qt6-tools-dev-tools \
  qml6-module-qtqml \
  qml6-module-qtqml-models \
  qml6-module-qtqml-workerscript \
  qml6-module-qtquick \
  qml6-module-qtquick-window \
  qml6-module-qtquick-controls \
  qml6-module-qtquick-layouts \
  qml6-module-qtquick-templates \
  libgl1-mesa-dev \
  libglu1-mesa-dev \
  libxkbcommon-dev \
  libxkbcommon-x11-dev
```

For **Arch Linux**:

```bash
sudo pacman -S base-devel cmake git qt6-base qt6-declarative qt6-tools
```

For **Fedora**:

```bash
sudo dnf install gcc-c++ cmake git qt6-qtbase-devel qt6-qtdeclarative-devel qt6-qttools-devel
```

## Build

### Linux / macOS

```bash
git clone https://github.com/SmetanaPrototype/QML_motion.git
cd QML_motion

cmake -B build -S . -DCMAKE_BUILD_TYPE=Release
cmake --build build -j$(nproc)

./build/motion
```

### Windows

```powershell
git clone https://github.com/SmetanaPrototype/QML_motion.git
cd QML_motion

cmake -B build -S . -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release

.\build\Release\motion.exe
```

If Qt is not in `PATH`, pass its location explicitly:

```powershell
cmake -B build -S . -DCMAKE_PREFIX_PATH="C:\Qt\6.8.2\msvc2022_64"
```

## Download

Prebuilt binaries are available in the [Releases](https://github.com/SmetanaPrototype/QML_motion/releases) section:

- **Windows**: `motion-Windows-x64.zip` — extract and run `motion.exe`
- **Linux**: `motion-Linux-x86_64.AppImage` — `chmod +x` and run

### Running the Linux AppImage

```bash
chmod +x motion-Linux-x86_64.AppImage
./motion-Linux-x86_64.AppImage
```

If your distribution lacks FUSE (Ubuntu 24.04+ by default):

```bash
./motion-Linux-x86_64.AppImage --appimage-extract-and-run
```

## License

MIT
