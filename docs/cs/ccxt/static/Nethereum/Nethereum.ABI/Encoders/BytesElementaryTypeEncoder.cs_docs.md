# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/BytesElementaryTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/BytesElementaryTypeEncoder.cs`
- **Size**: 2,225 bytes
- **Lines**: 75
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Linq;

namespace Nethereum.ABI.Encoders
{
    public class BytesElementaryTypeEncoder : ITypeEncoder
    {
        private readonly int _size;

        public BytesElementaryTypeEncoder(int size)
        {
            if(size > 32) throw new ArgumentException("bytes(Number) for an elementary type can only be a Maximum of 32");
            this._size = size;
        }

        public byte[] Encode(object value)
        {
            //default to false, this is a byte array we are not responsible for endianism
            return Encode(value, false);
        }

        public byte[] EncodePacked(object value)
        {
            if (_size == 1 && value is byte)
            {
                value = new byte[1] { (byte)value };
            }

            if (_size == 16 && value is Guid)
            {
                value = ((Guid)value).ToByteArray();
            }

            if (!(value is byte[]))
                throw new Exception("byte[] value expected for type 'bytes'");
            var byteArray = (byte[])value;

            if (byteArray.Length != _size)
                throw new Exception("byte[] size expected to be " + _size);

            return byteArray;

        }

        public byte[] Encode(object value, bool checkEndian)
        {
            if(_size == 1 && value is byte)
            {
                value = new byte[1] { (byte)value };
            }

            if (_size == 16 && value is Guid)
            {
                value = ((Guid) value).ToByteArray();
            }

            if (!(value is byte[]))
                throw new Exception("byte[] value expected for type 'bytes'");
            var byteArray = (byte[])value;

            if (byteArray.Length != _size)
                throw new Exception("byte[] size expected to be " + _size);

            var returnArray = new byte[((byteArray.Length - 1) / 32 + 1) * 32]; // padding 32 bytes

            //It should always be Big Endian.
            if (BitConverter.IsLittleEndian && checkEndian)
                byteArray = byteArray.Reverse().ToArray();

            Array.Copy(byteArray, 0, returnArray, 0, byteArray.Length);

            return returnArray;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/BytesElementaryTypeEncoder.cs`.

**Classes defined**: BytesElementaryTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 56
- Comment lines: 2
- Blank lines: 17

### Main Components

**Classes** (1):
- `BytesElementaryTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

