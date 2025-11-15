# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/BytesElementaryType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/BytesElementaryType.cs`
- **Size**: 361 bytes
- **Lines**: 14
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class BytesElementaryType : ABIType
    {
        public BytesElementaryType(string name, int size) : base(name)
        {
            Decoder = new BytesElementaryTypeDecoder(size);
            Encoder = new BytesElementaryTypeEncoder(size);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/BytesElementaryType.cs`.

**Classes defined**: BytesElementaryType



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 13
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `BytesElementaryType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

