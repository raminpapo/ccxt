# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/ContractUtils.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/ContractUtils.cs`
- **Size**: 2,816 bytes
- **Lines**: 70
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Numerics;

using Nethereum.Hex.HexConvertors.Extensions;
// using Nethereum.RLP;

namespace Nethereum.Util
{
    public static class ContractUtils
    {
        // public static string CalculateContractAddress(string address, BigInteger nonce)
        // {
        //     if (string.IsNullOrEmpty(address))
        //     {
        //         throw new System.ArgumentException($"'{nameof(address)}' cannot be null or empty.", nameof(address));
        //     }

        //     var sha3 = new Sha3Keccack();
        //     return
        //         sha3.CalculateHash(RLP.RLP.EncodeList(RLP.RLP.EncodeElement(address.HexToByteArray()),
        //                 RLP.RLP.EncodeElement(nonce.ToBytesForRLPEncoding()))).ToHex().Substring(24)
        //             .ConvertToEthereumChecksumAddress();
        // }

        public static string CalculateCreate2AddressMinimalProxy(string address, string saltHex,
            string deploymentAddress)
        {
            if (string.IsNullOrEmpty(deploymentAddress))
            {
                throw new System.ArgumentException($"'{nameof(deploymentAddress)}' cannot be null or empty.",
                    nameof(deploymentAddress));
            }

            var bytecode = "363d3d373d3d3d363d73" + deploymentAddress.RemoveHexPrefix() +
                           "5af43d82803e903d91602b57fd5bf3";
            return CalculateCreate2Address(address, saltHex, bytecode);
        }

        public static string CalculateCreate2Address(string address, string saltHex, string byteCodeHex)
        {
            var sha3 = new Sha3Keccack();
            return CalculateCreate2AddressUsingByteCodeHash(address, saltHex, sha3.CalculateHashFromHex(byteCodeHex));
        }


        public static string CalculateCreate2AddressUsingByteCodeHash(string address, string saltHex, string byteCodeHexHash)
        {
            if (string.IsNullOrEmpty(address))
            {
                throw new System.ArgumentException($"'{nameof(address)}' cannot be null or empty.", nameof(address));
            }

            if (string.IsNullOrEmpty(saltHex))
            {
                throw new System.ArgumentException($"'{nameof(saltHex)}' cannot be null or empty.", nameof(saltHex));
            }

            if (saltHex.EnsureHexPrefix().Length != 66)
            {
                throw new System.ArgumentException($"'{nameof(saltHex)}' needs to be 32 bytes", nameof(saltHex));
            }
            //ensure the address is a checksum address for hex hashing
            address = address.ConvertToEthereumChecksumAddress();

            var sha3 = new Sha3Keccack();
            return sha3.CalculateHashFromHex("0xff", address, saltHex, byteCodeHexHash)
                .Substring(24).ConvertToEthereumChecksumAddress();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/ContractUtils.cs`.

**Classes defined**: ContractUtils



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 44
- Comment lines: 14
- Blank lines: 12

### Main Components

**Classes** (1):
- `ContractUtils`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

