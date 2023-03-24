# Supported Languages

The table below shows the programming languages and the versions supported by Arcan.

| **Programming Language** | **Supported versions** | **Details** |
|---|---|---|
| Java | Java 17 and earlier | Java 18+ may work. |
| C | C17 and earlier | C17 is the latest C standard. |
| C++ | C++ 11 and earlier | Keywords and syntax introduced is newer standards is not yet supported. |
| C# | .NET 6 (via Mono)\* <br>.NET 7 (planned)\* | Projects that depend on Windows-only components are not supported (e.g. Windows Forms) by the trial and cloud versions.<br>Custom installations are required in such cases. |
| Python | Python 3.11 or earlier |  |

!!! warning

    \* Arcan (trial and cloud) is distributed as a Docker container based on Linux. This severely limits the supported .NET projects. You could still analyse these projects but it is likely that the results are incomplete.
