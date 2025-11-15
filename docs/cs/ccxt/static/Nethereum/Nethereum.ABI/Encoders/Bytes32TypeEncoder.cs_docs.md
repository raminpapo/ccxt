# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/Bytes32TypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/Bytes32TypeEncoder.cs`
- **Size**: 1,927 bytes
- **Lines**: 58
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Numerics;
using System.Text;
using Nethereum.ABI.Util;

namespace Nethereum.ABI.Encoders
{
    public class Bytes32TypeEncoder : ITypeEncoder
    {
        private readonly IntTypeEncoder _intTypeEncoder;

        public Bytes32TypeEncoder()
        {
            _intTypeEncoder = new IntTypeEncoder();
        }

        public byte[] Encode(object value)
        {
            if (value is BigInteger bigIntValue)
            {
                return _intTypeEncoder.EncodeInt(bigIntValue);
            }

            if (value.IsNumber())
            {
                var bigInt = BigInteger.Parse(value.ToString());
                return _intTypeEncoder.EncodeInt(bigInt);
            }

            var stringValue = value as string;
            if (stringValue != null)
            {
                var returnBytes = new byte[32];
                var bytes = Encoding.UTF8.GetBytes(stringValue);
                if(bytes.Length > 32) throw new ArgumentException("After retrieving the UTF8 bytes for the string, it is longer than 32 bytes, please using the string type, or a byte array if the string was a hex value");
                Array.Copy(bytes, 0, returnBytes, 0, bytes.Length);
                return returnBytes;
            }

            var bytesValue = value as byte[];
            if (bytesValue != null)
            {
                if (bytesValue.Length > 32) throw new ArgumentException("Expected byte array no bigger than 32 bytes");

                var returnArray = new byte[((bytesValue.Length - 1) / 32 + 1) * 32];
                Array.Copy(bytesValue, 0, returnArray, 0, bytesValue.Length);
                return returnArray;
            }

            throw new ArgumentException("Expected Numeric Type or String to be Encoded as Bytes32");
        }

        public byte[] EncodePacked(object value)
        {
            return Encode(value);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/Bytes32TypeEncoder.cs`.

**Classes defined**: Bytes32TypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 49
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `Bytes32TypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

