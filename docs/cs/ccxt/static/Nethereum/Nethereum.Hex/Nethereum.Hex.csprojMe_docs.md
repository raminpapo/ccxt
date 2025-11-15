# Documentation: cs/ccxt/static/Nethereum/Nethereum.Hex/Nethereum.Hex.csprojMe

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Hex/Nethereum.Hex.csprojMe`
- **Size**: 2,914 bytes
- **Lines**: 45
- **Type**: Unknown
- **Extension**: .csprojMe


## Original Source Code

```
﻿<Project Sdk="Microsoft.NET.Sdk">
  <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
  <PropertyGroup>
    <Description>HexTypes for encoding and encoding String, BigInteger, this is specific for Ethereum</Description>
    <AssemblyTitle>Nethereum.Hex</AssemblyTitle>
    <VersionPrefix>$(NethereumVersion)</VersionPrefix>
    <TargetFrameworks>$(DefaultFrameworksUnitySupport)</TargetFrameworks>
    <OutputType>Library</OutputType>
    <AssemblyName>Nethereum.Hex</AssemblyName> 
    <PackageId>Nethereum.Hex</PackageId>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="..\Nethereum.BigInteger.N351\BigInteger.cs" Link="BigInteger\BigInteger.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigIntegerCalculator.AddSub.cs" Link="BigInteger\BigIntegerCalculator.AddSub.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigIntegerCalculator.BitsBuffer.cs" Link="BigInteger\BigIntegerCalculator.BitsBuffer.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigIntegerCalculator.DivRem.cs" Link="BigInteger\BigIntegerCalculator.DivRem.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigIntegerCalculator.FastReducer.cs" Link="BigInteger\BigIntegerCalculator.FastReducer.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigIntegerCalculator.GcdInv.cs" Link="BigInteger\BigIntegerCalculator.GcdInv.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigIntegerCalculator.PowMod.cs" Link="BigInteger\BigIntegerCalculator.PowMod.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigIntegerCalculator.SquMul.cs" Link="BigInteger\BigIntegerCalculator.SquMul.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\BigNumber.cs" Link="BigInteger\BigNumber.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\FormatProvider.BigInteger.cs" Link="BigInteger\FormatProvider.BigInteger.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\FormatProvider.Number.cs" Link="BigInteger\FormatProvider.Number.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\FormatProvider.NumberBuffer.cs" Link="BigInteger\FormatProvider.NumberBuffer.cs" />
    <Compile Include="..\Nethereum.BigInteger.N351\NumericHelpers.cs" Link="BigInteger\NumericHelpers.cs" />
  </ItemGroup>

  <ItemGroup>
    <Folder Include="BigInteger\" />
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

This is a Unknown file located at `cs/ccxt/static/Nethereum/Nethereum.Hex/Nethereum.Hex.csprojMe`.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 41
- Comment lines: 0
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `BigInteger\BigIntegerCalculator.DivRem.cs` (referenced)
- `BigInteger\BigIntegerCalculator.AddSub.cs` (referenced)
- `..\Nethereum.BigInteger.N351\BigIntegerCalculator.DivRem.cs` (referenced)
- `BigInteger\BigInteger.cs` (referenced)
- `..\Nethereum.BigInteger.N351\BigInteger.cs` (referenced)
- `..\Nethereum.BigInteger.N351\BigIntegerCalculator.FastReducer.cs` (referenced)
- `BigInteger\BigIntegerCalculator.FastReducer.cs` (referenced)
- `BigInteger\BigIntegerCalculator.BitsBuffer.cs` (referenced)
- `..\Nethereum.BigInteger.N351\BigIntegerCalculator.BitsBuffer.cs` (referenced)
- `..\Nethereum.BigInteger.N351\BigIntegerCalculator.AddSub.cs` (referenced)



## Testing & Execution

**To execute this Unknown file:**

