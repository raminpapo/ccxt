# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/HashProviders/Sha3KeccackHashProvider.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/HashProviders/Sha3KeccackHashProvider.cs`
- **Size**: 244 bytes
- **Lines**: 13
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿
namespace Nethereum.Util.HashProviders
{
    public class Sha3KeccackHashProvider : IHashProvider
    {
        public byte[] ComputeHash(byte[] data)
        {
            return Sha3Keccack.Current.CalculateHash(data);
        }
    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/HashProviders/Sha3KeccackHashProvider.cs`.

**Classes defined**: Sha3KeccackHashProvider



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 11
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `Sha3KeccackHashProvider`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

