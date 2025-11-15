# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/EIP2612/EIP2612TypeFactory.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/EIP2612/EIP2612TypeFactory.cs`
- **Size**: 1,165 bytes
- **Lines**: 36
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.FunctionEncoding.Attributes;
using System;
using System.Collections.Generic;
using System.Numerics;
using System.Text;

namespace Nethereum.ABI.EIP712.EIP2612
{
    /// <summary>
    /// The type factory creates a new TypeDefinition to work with EIP2612.
    /// https://eips.ethereum.org/EIPS/eip-2612
    /// ERC-20 approvals via secp256k1 signatures
    /// This ERC extends the ERC-20 standard with a new function permit, which allows users to modify the allowance mapping using a signed message, instead of through msg.sender.
    /// 
    /// </summary>
    public static class EIP2612TypeFactory
    {
        public static TypedData<Domain> GetTypedDefinition()
        {
            return new TypedData<Domain>
            {
                Domain = new Domain
                {
                    Name = null,
                    Version = "1",
                    ChainId = 1,
                    VerifyingContract = null
                },
                Types = MemberDescriptionFactory.GetTypesMemberDescription(typeof(Domain), typeof(Permit)),
                PrimaryType = nameof(Permit),
            };
        }
    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/EIP2612/EIP2612TypeFactory.cs`.

**Classes defined**: EIP2612TypeFactory

**Functions defined**: permit



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 26
- Comment lines: 7
- Blank lines: 3

### Main Components

**Classes** (1):
- `EIP2612TypeFactory`

**Functions** (1):
- `permit()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

