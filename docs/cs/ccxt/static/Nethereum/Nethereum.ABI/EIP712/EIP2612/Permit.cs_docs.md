# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/EIP2612/Permit.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/EIP2612/Permit.cs`
- **Size**: 631 bytes
- **Lines**: 27
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.FunctionEncoding.Attributes;
using System.Numerics;

namespace Nethereum.ABI.EIP712.EIP2612
{
    [Struct("Permit")]
    public class Permit
    {
        [Parameter("address", "owner", 1)]
        public string Owner { get; set; }

        [Parameter("address", "spender", 2)]
        public string Spender { get; set; }

        [Parameter("uint256", "value", 3)]
        public BigInteger Value { get; set; }

        [Parameter("uint256", "nonce", 4)]
        public BigInteger Nonce { get; set; }

        [Parameter("uint256", "deadline", 5)]
        public BigInteger Deadline { get; set; }

    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/EIP2612/Permit.cs`.

**Classes defined**: Permit



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 19
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (1):
- `Permit`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

