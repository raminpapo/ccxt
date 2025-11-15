# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/ABIValue.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/ABIValue.cs`
- **Size**: 442 bytes
- **Lines**: 20
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Nethereum.ABI
{
    public class ABIValue
    {
        public ABIValue(ABIType abiType, object value)
        {
            ABIType = abiType;
            Value = value;
        }

        public ABIValue(string abiType, object value)
        {
            ABIType = ABIType.CreateABIType(abiType);
            Value = value;
        }

        public ABIType ABIType { get; set; }
        public object Value { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/ABIValue.cs`.

**Classes defined**: ABIValue



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 18
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `ABIValue`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

