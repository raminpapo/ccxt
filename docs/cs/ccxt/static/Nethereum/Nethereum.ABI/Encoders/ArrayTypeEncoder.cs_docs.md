# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/ArrayTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/ArrayTypeEncoder.cs`
- **Size**: 882 bytes
- **Lines**: 28
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Collections;
using System.Linq;

namespace Nethereum.ABI.Encoders
{
    public abstract class ArrayTypeEncoder : ITypeEncoder
    {
        public byte[] Encode(object value)
        {
            var array = value as IEnumerable;
            if ((array != null) && !(value is string))
                return EncodeList(array.Cast<object>().ToList());
            throw new Exception("Array value expected for type");
        }

        public byte[] EncodePacked(object value)
        {
            var array = value as IEnumerable;
            if ((array != null) && !(value is string))
                return EncodeListPacked(array.Cast<object>().ToList());
            throw new Exception("Array value expected for type");
        }

        public abstract byte[] EncodeList(IList l);
        public abstract byte[] EncodeListPacked(IList l);
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/ArrayTypeEncoder.cs`.

**Classes defined**: ArrayTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 25
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `ArrayTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

