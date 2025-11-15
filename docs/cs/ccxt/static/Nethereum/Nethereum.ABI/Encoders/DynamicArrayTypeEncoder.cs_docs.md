# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/DynamicArrayTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/DynamicArrayTypeEncoder.cs`
- **Size**: 1,799 bytes
- **Lines**: 54
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Collections;
using Nethereum.ABI.FunctionEncoding;
using Nethereum.ABI.Util;
using Nethereum.Util;

namespace Nethereum.ABI.Encoders
{
    public class DynamicArrayTypeEncoder : ArrayTypeEncoder
    {
        private readonly ABIType _elementType;
        private readonly IntTypeEncoder _intTypeEncoder;

        public DynamicArrayTypeEncoder(ABIType elementType)
        {
           
            this._elementType = elementType;
            _intTypeEncoder = new IntTypeEncoder();
        }

        public override byte[] EncodeList(IList l)
        {
            if (_elementType.IsDynamic())
            {
                var elems = new byte[l.Count + 1 + l.Count][];
                elems[0] = _intTypeEncoder.EncodeInt(l.Count);

                var currentSize = 0;
                for (var i = 0; i < l.Count; i++)
                {
                    elems[i + 1] = _intTypeEncoder.EncodeInt((l.Count * 32) + currentSize); //location element
                    elems[i + 1 + l.Count] = _elementType.Encode(l[i]);
                    currentSize = currentSize + elems[i + 1 + l.Count].Length;
                }
                return ByteUtil.Merge(elems);
            }
            else
            {
                var elems = new byte[l.Count + 1][];
                elems[0] = _intTypeEncoder.EncodeInt(l.Count);
                for (var i = 0; i < l.Count; i++)
                    elems[i + 1] = _elementType.Encode(l[i]);
                return ByteUtil.Merge(elems);
            }
        }

        public override byte[] EncodeListPacked(IList l)
        {
            var elems = new byte[l.Count][];
            for (var i = 0; i < l.Count; i++)
                elems[i] = _elementType.Encode(l[i]);
            return ByteUtil.Merge(elems);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/DynamicArrayTypeEncoder.cs`.

**Classes defined**: DynamicArrayTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 48
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `DynamicArrayTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

