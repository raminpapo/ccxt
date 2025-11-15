# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/ByteArrayConvertors/HexToByteArrayConvertor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/ByteArrayConvertors/HexToByteArrayConvertor.cs`
- **Size**: 299 bytes
- **Lines**: 14
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.Hex.HexConvertors.Extensions;

namespace Nethereum.Util.ByteArrayConvertors
{
    public class HexToByteArrayConvertor : IByteArrayConvertor<string>
    {
        public byte[] ConvertToByteArray(string data)
        {
            return data.HexToByteArray();
        }
    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/ByteArrayConvertors/HexToByteArrayConvertor.cs`.

**Classes defined**: HexToByteArrayConvertor



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 11
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `HexToByteArrayConvertor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

