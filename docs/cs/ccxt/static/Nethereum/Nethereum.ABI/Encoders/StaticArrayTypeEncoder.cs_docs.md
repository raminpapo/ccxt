# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/StaticArrayTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/StaticArrayTypeEncoder.cs`
- **Size**: 1,943 bytes
- **Lines**: 58
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Collections;
using Nethereum.ABI.Util;
using Nethereum.Util;

namespace Nethereum.ABI.Encoders
{
    public class StaticArrayTypeEncoder : ArrayTypeEncoder
    {
        private readonly int arraySize;
        private readonly ABIType elementType;
        private readonly IntTypeEncoder intTypeEncoder;

        public StaticArrayTypeEncoder(ABIType elementType, int arraySize)
        {
            this.elementType = elementType;
            this.arraySize = arraySize;
            intTypeEncoder = new IntTypeEncoder();
        }

        public override byte[] EncodeList(IList l)
        {
            if (l.Count != arraySize)
                throw new Exception("List size (" + l.Count + ") != " + arraySize);
            
            if (elementType.IsDynamic())
            {
                var elems = new byte[arraySize + arraySize][];
                var currentSize = 0;
                for (var i = 0; i < l.Count; i++)
                {
                    elems[i] = intTypeEncoder.EncodeInt((l.Count * 32) + currentSize);
                    elems[i + l.Count] = elementType.Encode(l[i]);
                    currentSize = currentSize + elems[i + l.Count].Length;
                }
                return ByteUtil.Merge(elems);
            }
            else
            {
                var elems = new byte[arraySize][];
                for (var i = 0; i < l.Count; i++)
                    elems[i] = elementType.Encode(l[i]);
                return ByteUtil.Merge(elems);
            }
        }

        public override byte[] EncodeListPacked(IList l)
        {
            if (l.Count != arraySize)
                throw new Exception("List size (" + l.Count + ") != " + arraySize);

            var elems = new byte[arraySize][];
            for (var i = 0; i < l.Count; i++)
                elems[i] = elementType.Encode(l[i]);
            return ByteUtil.Merge(elems);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/StaticArrayTypeEncoder.cs`.

**Classes defined**: StaticArrayTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 52
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `StaticArrayTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

