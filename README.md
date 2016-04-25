#PowerShell for Docker
The goal of this project is to create a PowerShell module for the [Docker Engine]( https://github.com/docker/docker/), which can be utilized as an alternative or in conjunction with the Docker client (CLI).

##Requirements and Goals
### Requirements
1.	Must follow the Docker Remote API interop and breaking change policy (https://docs.docker.com/engine/breaking_changes/)
2.	Must work locally or remotely, with remote following appropriate authentication and security mechanisms (i.e. TLS).

### Goals
* Follow the PowerShell design guidelines (https://msdn.microsoft.com/en-us/library/ms714657(v=vs.85).aspx).
* Follow the general design and usage patterns of Docker
* Must remain CoreCLR compliant (see links below). Note that given the current requirements for the Docker.DotNet.X509, the project is still compiling for net46 instead of netstandard.  However, once updated implementation for TLS authentication is present, the project will be updated for netstarded and expected to compile and function on Nano Server using the .NET Core CLR and Core Libraries available there.


####.Net Core and Core PowerShell Resources
##### GitHub Repo’s for .Net Core CLR and .Net Core Libraries
* https://github.com/dotnet/coreclr
* https://github.com/dotnet/core

##### Good Resources Explaining .Net Core
* https://blogs.msdn.microsoft.com/dotnet/2016/02/10/porting-to-net-core/
* https://technet.microsoft.com/en-us/library/hh849695.aspx

##Compilation
To compile this project, execute build.cmd from the local folder in a command prompt that includes dotnet CLI (https://github.com/dotnet/cli) in the PATH. This will produce the module dll at ".\artifacts\bin\Docker.PowerShell\Debug\net46\Docker.PowerShell.dll" in the project folder.

##High Level Design
The PowerShell module for Docker is built on top of the Docker Engine REST Interface (https://docs.docker.com/engine/reference/api/docker_remote_api/).
