# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/StringBytes32Decoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/StringBytes32Decoder.cs`
- **Size**: 470 bytes
- **Lines**: 15
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Linq;

namespace Nethereum.ABI.Decoders
{
    public class StringBytes32Decoder : ICustomRawDecoder<string>
    {
        public string Decode(byte[] output)
        {
            if (output.Length > 32)
                //assuming that first 32 is the data index as this is the raw data
                return new StringTypeDecoder().Decode(output.Skip(32).ToArray());
            return new Bytes32TypeDecoder().Decode<string>(output);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/StringBytes32Decoder.cs`.

**Classes defined**: StringBytes32Decoder



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 13
- Comment lines: 1
- Blank lines: 1

### Main Components

**Classes** (1):
- `StringBytes32Decoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

