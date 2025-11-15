# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/Sha3Keccack.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/Sha3Keccack.cs`
- **Size**: 1,027 bytes
- **Lines**: 35
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Linq;
using System.Text;
using Nethereum.Hex.HexConvertors.Extensions;
using Nethereum.Util.Keccak;


namespace Nethereum.Util
{
    public class Sha3Keccack
    {
        public static Sha3Keccack Current { get; } = new Sha3Keccack();

        public string CalculateHash(string value)
        {
            var input = Encoding.UTF8.GetBytes(value);
            var output = CalculateHash(input);
            return output.ToHex();
        }

        public string CalculateHashFromHex(params string[] hexValues)
        {
            var joinedHex = string.Join("", hexValues.Select(x => x.RemoveHexPrefix()).ToArray());
            return CalculateHash(joinedHex.HexToByteArray()).ToHex();
        }

        public byte[] CalculateHash(byte[] value)
        {
            var digest = new KeccakDigest(256);
            var output = new byte[digest.GetDigestSize()];
            digest.BlockUpdate(value, 0, value.Length);
            digest.DoFinal(output, 0);
            return output;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/Sha3Keccack.cs`.

**Classes defined**: Sha3Keccack



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 30
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `Sha3Keccack`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

