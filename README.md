# LHM-CppExport

* Exporter - C# Library that exposes functions that returns information as C# string's from [LibreHardwareMonitor](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor)

* CPPdll - Managed C++ Library that exposes functions from Exporter and returns information as std::string's

* CppTest - Unmanaged C++ program that prints the returned strings from the functions in CPPdll to console

## To Create release DLL's and .lib

* LibreHardwareMonitor (currently 0.9.6, which no longer ships the WinRing0 driver) and other dependencies are restored automatically with NuGet (`PackageReference`). Use `msbuild -restore` or build from Visual Studio 2022.

* LibreHardwareMonitorLib 0.9.6+ ships its DLL only under `runtimes\win-x64`; Exporter.csproj copies it explicitly, and CPPdll post-build copies all Exporter dependencies to the output folder (x64 Release only).

* Some sensors on some CPUs need the separate [PawnIO](https://pawnio.eu) driver installed.

1. Open solution with Visual Studio 2022

2. Set Release - x64

3. Build CPPdll

* For building btop4win LHM version, copy all ".dll" and ".lib" from "x64\Release" (all of them, including LibreHardwareMonitorLib.dll and its dependencies) to "external" folder in top-level of [btop4win](https://github.com/aristocratos/btop4win).