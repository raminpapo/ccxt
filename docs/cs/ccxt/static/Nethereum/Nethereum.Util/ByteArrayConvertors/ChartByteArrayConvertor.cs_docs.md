# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/ByteArrayConvertors/ChartByteArrayConvertor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/ByteArrayConvertors/ChartByteArrayConvertor.cs`
- **Size**: 285 bytes
- **Lines**: 14
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Text;

namespace Nethereum.Util.ByteArrayConvertors
{
    public class ChartByteArrayConvertor : IByteArrayConvertor<char>
    {
        public byte[] ConvertToByteArray(char data)
        {
            return Encoding.UTF8.GetBytes(new[] { data });
        }
    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/ByteArrayConvertors/ChartByteArrayConvertor.cs`.

**Classes defined**: ChartByteArrayConvertor



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 11
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `ChartByteArrayConvertor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

