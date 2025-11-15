# Documentation: cs/ccxt/static/Nethereum/Nethereum.Signer.EIP712/Nethereum.Signer.EIP712.csproj

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Signer.EIP712/Nethereum.Signer.EIP712.csproj`
- **Size**: 1,461 bytes
- **Lines**: 29
- **Type**: Unknown
- **Extension**: .csproj


## Original Source Code

```
<Project Sdk="Microsoft.NET.Sdk">
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
    <PropertyGroup>
        <Description>Nethereum signer library to sign and encode messages according to EIP-712</Description>
        <AssemblyTitle>Nethereum.Signer.EIP712</AssemblyTitle>
        <VersionPrefix>$(NethereumVersion)</VersionPrefix>
        <TargetFrameworks>$(DefaultFrameworks)</TargetFrameworks>
        <AssemblyName>Nethereum.Signer.EIP712</AssemblyName>
        <PackageId>Nethereum.Signer.EIP712</PackageId>
        <PackageTags>Netherum;Ethereum;Blockchain;EIP-712;Signer</PackageTags>
    </PropertyGroup>

    <ItemGroup>
      <ProjectReference Include="..\Nethereum.ABI\Nethereum.ABI.csproj" />
      <ProjectReference Include="..\Nethereum.Hex\Nethereum.Hex.csproj" />
      <ProjectReference Include="..\Nethereum.Signer\Nethereum.Signer.csproj" />
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

This is a Unknown file located at `cs/ccxt/static/Nethereum/Nethereum.Signer.EIP712/Nethereum.Signer.EIP712.csproj`.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 25
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

