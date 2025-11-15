# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/Nethereum.Util.csprojRem

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/Nethereum.Util.csprojRem`
- **Size**: 1,222 bytes
- **Lines**: 27
- **Type**: Unknown
- **Extension**: .csprojRem


## Original Source Code

```
﻿<Project Sdk="Microsoft.NET.Sdk">
  <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
  <PropertyGroup>
    <Description>Nethereum Utilities library, including Sha3 Keccack encoding and Address Checksum</Description>
    <AssemblyTitle>Nethereum.Util</AssemblyTitle>
    <VersionPrefix>$(NethereumVersion)</VersionPrefix>
    <TargetFrameworks>$(DefaultFrameworksUnitySupport)</TargetFrameworks>
    <AssemblyName>Nethereum.Util</AssemblyName>
    <PackageId>Nethereum.Util</PackageId>
    <PackageTags>Netherum;Ethereum;Blockchain</PackageTags>
  </PropertyGroup>

  <ItemGroup>
    <ProjectReference Include="..\Nethereum.Hex\Nethereum.Hex.csproj" />
    <ProjectReference Include="..\Nethereum.RLP\Nethereum.RLP.csproj" />
  </ItemGroup>

  <PropertyGroup Condition=" '$(TargetFramework)' != 'net35' And '$(TargetUnityNet461AOT)' != 'true'">
    <SignAssembly>true</SignAssembly>
    <AssemblyOriginatorKeyFile>..\..\NethereumKey.snk</AssemblyOriginatorKeyFile>
  </PropertyGroup>
  <ItemGroup Condition=" '$(TargetFramework)' != 'net35' And '$(TargetUnityNet461AOT)' != 'true'">
    <None Include="..\..\NethereumKey.snk" />
  </ItemGroup>

</Project>

```

## High-Level Overview

This is a Unknown file located at `cs/ccxt/static/Nethereum/Nethereum.Util/Nethereum.Util.csprojRem`.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 23
- Comment lines: 0
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `..\..\NethereumKey.snk` (referenced)



## Testing & Execution

**To execute this Unknown file:**

