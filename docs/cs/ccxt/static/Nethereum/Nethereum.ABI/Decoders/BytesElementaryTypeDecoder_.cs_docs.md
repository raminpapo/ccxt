# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BytesElementaryTypeDecoder .cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BytesElementaryTypeDecoder .cs`
- **Size**: 1,117 bytes
- **Lines**: 40
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Linq;

namespace Nethereum.ABI.Decoders
{
    public class BytesElementaryTypeDecoder : TypeDecoder
    {
        private readonly int _size;

        public BytesElementaryTypeDecoder(int size)
        {
            _size = size;
        }

        public override object Decode(byte[] encoded, Type type)
        {
            if (!IsSupportedType(type)) throw new NotSupportedException(type + " is not supported");

            var returnArray = encoded.Take(_size).ToArray();

            if (_size == 1 && type == typeof(byte)) return returnArray[0];

            if (_size == 16 && type == typeof(Guid)) return new Guid(returnArray);

            return returnArray;
        }

        public override Type GetDefaultDecodingType()
        {
            return typeof(byte[]);
        }

        public override bool IsSupportedType(Type type)
        {
            if (_size == 1) return type == typeof(byte[]) || type == typeof(byte);
            if (_size == 16) return type == typeof(byte[]) || type == typeof(Guid);
            return type == typeof(byte[]);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/BytesElementaryTypeDecoder .cs`.

**Classes defined**: BytesElementaryTypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 31
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `BytesElementaryTypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

