# .NET Library for Native Apps

# Steps from scratch

- Create a new project
  ```sh
  dotnet new classlib -o DotNetLib
  ```
- add NativeAOT support by creating a nuget config
  ```sh
  cd DotNetLib
  dotnet new nugetconfig
  ```
- Add the following to the `nuget.config` file:
  ```xml
  <add key="dotnet-experimental" value="https://pkgs.dev.azure.com/dnceng/public/  _packaging/dotnet-experimental/nuget/v3/index.json" />
  ```
- add a reference to the compiler
  ```sh
  dotnet add package Microsoft.DotNet.ILCompiler -v 7.0.0-*
  ```
- then you can publish the dll like this
  ```sh
  dotnet publish /p:NativeLib=Shared /p:SelfContained=true -r <RID> -c <Configuration>
  ```