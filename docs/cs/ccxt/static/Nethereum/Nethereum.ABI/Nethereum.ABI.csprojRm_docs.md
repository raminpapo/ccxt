# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Nethereum.ABI.csprojRm

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Nethereum.ABI.csprojRm`
- **Size**: 1,111 bytes
- **Lines**: 25
- **Type**: Unknown
- **Extension**: .csprojRm


## Original Source Code

```
﻿<Project Sdk="Microsoft.NET.Sdk">
	<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
	<PropertyGroup>
		<Description>Encoding and decoding of ABI Types, functions, events of Ethereum contracts</Description>
		<AssemblyTitle>Nethereum.ABI</AssemblyTitle>
		<Version>$(NethereumVersion)</Version>
		<TargetFrameworks>$(DefaultFrameworksUnitySupport)</TargetFrameworks>
		<AssemblyName>Nethereum.ABI</AssemblyName>
		<PackageId>Nethereum.ABI</PackageId>
	</PropertyGroup>
	<ItemGroup>
		<ProjectReference Include="..\Nethereum.Hex\Nethereum.Hex.csproj" />
		<ProjectReference Include="..\Nethereum.Util\Nethereum.Util.csproj" />
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

This is a Unknown file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Nethereum.ABI.csprojRm`.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 22
- Comment lines: 0
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `..\..\NethereumKey.snk` (referenced)



## Testing & Execution

**To execute this Unknown file:**

