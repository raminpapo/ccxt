# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ByteCodeSwarmExtractor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ByteCodeSwarmExtractor.cs`
- **Size**: 1,549 bytes
- **Lines**: 48
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Text.RegularExpressions;

namespace Nethereum.ABI.FunctionEncoding
{
    public class ByteCodeSwarmExtractor
    {
        public const string bzzr0_Hex = "627a7a7230";
        public const string Prefix_bzzr0_Hex = "a165";
        public const string Suffix_bzzr0_Hex = "5820";
        public const string Prefix_Address_Hex = Prefix_bzzr0_Hex + bzzr0_Hex + Suffix_bzzr0_Hex;
        public const string Suffix_Address_Hex = "0029";

        public string GetSwarmAddress(string byteCode)
        {
     
            var r = new Regex("(?<=a165627a7a72305820)(.*[0-9a-fA-F]{64})(?=0029)");
      
            if (r.IsMatch(byteCode))
            {
                return r.Match(byteCode).Value;
            }

            return null;
        }

        private string GetSwarmPaddedString(string byteCode)
        {
            return Prefix_Address_Hex + GetSwarmAddress(byteCode) + Suffix_Address_Hex;
        }

        public string GetByteCodeIncludingSwarmAddressPart(string byteCode)
        {
            var paddedSwarm = GetSwarmPaddedString(byteCode);
            return byteCode.Substring(0, byteCode.IndexOf(paddedSwarm) + paddedSwarm.Length);
        }

        public string GetByteCodeExludingSwarmAddressPart(string byteCode)
        {
            var paddedSwarm = GetSwarmPaddedString(byteCode);
            return byteCode.Substring(0, byteCode.IndexOf(paddedSwarm));
        }

        public bool HasSwarmAddress(string byteCode)
        {
            return GetSwarmAddress(byteCode) != null;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ByteCodeSwarmExtractor.cs`.

**Classes defined**: ByteCodeSwarmExtractor



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 39
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `ByteCodeSwarmExtractor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

