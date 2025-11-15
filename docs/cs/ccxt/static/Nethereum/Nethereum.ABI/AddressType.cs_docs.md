# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/AddressType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/AddressType.cs`
- **Size**: 379 bytes
- **Lines**: 15
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class AddressType : ABIType
    {
        public AddressType() : base("address")
        {
            //this will need to be only a string type one, converting to hex
            Decoder = new AddressTypeDecoder();
            Encoder = new AddressTypeEncoder();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/AddressType.cs`.

**Classes defined**: AddressType



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 13
- Comment lines: 1
- Blank lines: 1

### Main Components

**Classes** (1):
- `AddressType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

