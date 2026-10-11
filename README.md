# C++ workspace

C++20, MSVC, CMake and Ninja. Source lives in `src/`, generated builds in
`out/`, and release ZIPs in `dist/`. Generated files are ignored by Git.

From PowerShell in this folder:

```powershell
powershell -ExecutionPolicy Bypass -File scripts/dev.ps1 run
powershell -ExecutionPolicy Bypass -File scripts/dev.ps1 test
powershell -ExecutionPolicy Bypass -File scripts/dev.ps1 package
```

Use `-Configuration Release` for optimized builds. Packaging builds and tests
Release, then writes a ZIP to `dist/`. Extract it on another Windows x64 PC
and run `bin/cpp_app.exe`. The sample uses the static MSVC runtime. Future
third-party libraries may need additional files or licenses in the package.

In Visual Studio Code, use Ctrl+Shift+B to build, or Terminal > Run Task to
run, test, or package. Tasks load the compiler environment automatically.

Edit `src/main.cpp` to start. Add new `.cpp` files to `add_executable` in
`CMakeLists.txt`. You can remove the generated `out/` and `dist/` folders
when you want a fresh build; the commands recreate them.

Prerequisites: stable Visual Studio Build Tools with the C++ workload and
CMake tools (listed in `.vsconfig`). The script discovers the installation
and loads its developer environment without changing your global PATH.

Install or update the stable toolchain using Windows Package Manager:

```powershell
winget install --exact --id Microsoft.VisualStudio.BuildTools --override "--quiet --wait --norestart --add Microsoft.VisualStudio.Workload.VCTools --includeRecommended"
winget upgrade --exact --id Microsoft.VisualStudio.BuildTools
```

Review available updates periodically. No background updater or reboot is scheduled.
Run `powershell -ExecutionPolicy Bypass -File scripts/update-tools.ps1` to
update this C++ toolchain and Git only.
