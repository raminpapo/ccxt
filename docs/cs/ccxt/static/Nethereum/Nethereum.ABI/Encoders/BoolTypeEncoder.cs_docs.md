# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/BoolTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/BoolTypeEncoder.cs`
- **Size**: 770 bytes
- **Lines**: 28
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Nethereum.ABI.Encoders
{
    public class BoolTypeEncoder : ITypeEncoder
    {
        private readonly IntTypeEncoder _intTypeEncoder;

        public BoolTypeEncoder()
        {
            _intTypeEncoder = new IntTypeEncoder(false,8);
        }

        public byte[] Encode(object value)
        {
            if (!(value is bool))
                throw new Exception("Wrong value for bool type: " + value);
            return _intTypeEncoder.Encode((bool) value ? 1 : 0);
        }

        public byte[] EncodePacked(object value)
        {
            if (!(value is bool))
                throw new Exception("Wrong value for bool type: " + value);
            return _intTypeEncoder.EncodePacked((bool)value ? 1 : 0);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/BoolTypeEncoder.cs`.

**Classes defined**: BoolTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 24
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `BoolTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

