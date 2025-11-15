# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/StringTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/StringTypeEncoder.cs`
- **Size**: 849 bytes
- **Lines**: 33
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Text;

namespace Nethereum.ABI.Encoders
{
    public class StringTypeEncoder : ITypeEncoder
    {
        private readonly BytesTypeEncoder byteTypeEncoder;

        public StringTypeEncoder()
        {
            byteTypeEncoder = new BytesTypeEncoder();
        }

        public byte[] Encode(object value)
        {
            if (!(value is string))
                throw new Exception("String value expected for type 'string'");

            var bytes = Encoding.UTF8.GetBytes((string) value);

            return byteTypeEncoder.Encode(bytes, false);
        }

        public byte[] EncodePacked(object value)
        {
            if (!(value is string))
                throw new Exception("String value expected for type 'string'");

            return Encoding.UTF8.GetBytes((string)value);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/StringTypeEncoder.cs`.

**Classes defined**: StringTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 26
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `StringTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

