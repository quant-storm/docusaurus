---
sidebar_position: 7
---

# Setting Up the Indicator Project


## The File `*.csproj`

The [.csproj][20] file is the configuration file for your [C#][0] project. 
  It defines the settings and properties used during the build 
  process. Here’s a breakdown of each section in a typical [.csproj][20]
  file for an indicator project

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project Sdk="Microsoft.NET.Sdk">

  <!-- This section defines the project -->
  <PropertyGroup>
      <!-- Specifies the version of .NET the project targets -->
      <TargetFramework>net8</TargetFramework>

      <!-- Specifies the version of the C# language to use -->
      <LangVersion>latest</LangVersion>

      <!-- Prevents adding the target framework version to the output folder name -->
      <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>

      <!-- The project will be compiled to run on any CPU architecture -->
      <Platforms>AnyCPU</Platforms>

      <!-- Quantower property that defines the type of the algorithm -->
      <AlgoType>Indicator</AlgoType>

      <!-- The name of the output assembly after build -->
      <AssemblyName>HelloWorld</AssemblyName>

      <!-- The root namespace used throughout the project -->
      <RootNamespace>HelloWorld</RootNamespace>
  </PropertyGroup>

  <!-- 
    This section defines the output folder for the "Debug|AnyCPU" 
    configuration 
    -->
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
      <OutputPath>..\v1.142.6\..\..\Settings\Scripts\Indicators\HelloWorld</OutputPath>
  </PropertyGroup>

  <!-- 
    This section defines the output folder for the "Release|AnyCPU" 
    configuration 
    -->
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
      <OutputPath>..\v1.142.6\..\..\Settings\Scripts\Indicators\HelloWorld</OutputPath>
  </PropertyGroup>

  <!--  
    This section adds a reference to an external DLL, which is 
    required for the project 
    -->
  <ItemGroup>
      <Reference Include="TradingPlatform.BusinessLayer">
          <HintPath>..\v1.142.7\bin\TradingPlatform.BusinessLayer.dll</HintPath>
      </Reference>
  </ItemGroup>

</Project> 
```

### Properties and Conditions

```xml
<PropertyGroup>
  ...
</PropertyGroup>
```

> A project file typically needs to provide lots of different pieces of information in order to successfully build and deploy your projects. These pieces of information could include server names, connection strings, credentials, build configurations, source and destination file paths, and any other information you want to include to support customization.. [learn more][21]

### Items and Item Groups

```xml
<ItemGroup>
   ...
</ItemGroup>
```

> One of the important roles of the project file is to define the inputs to the build process. Typically, these inputs are files—code files, configuration files, command files, and any other files that you need to process or copy as part of the build process.. [learn more][22]

[0]: https://dotnet.microsoft.com/en-us/languages/csharp
[20]: https://learn.microsoft.com/en-us/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file
[21]: https://learn.microsoft.com/en-us/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file#items-and-item-groups
[22]: https://learn.microsoft.com/en-us/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file#properties-and-conditions
