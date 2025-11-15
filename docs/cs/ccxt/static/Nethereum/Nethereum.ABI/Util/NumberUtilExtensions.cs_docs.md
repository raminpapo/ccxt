# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Util/NumberUtilExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Util/NumberUtilExtensions.cs`
- **Size**: 564 bytes
- **Lines**: 20
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Nethereum.ABI.Util
{
    public static class NumberExtensions
    {
        public static bool IsNumber(this object value)
        {
            return value is sbyte
                   || value is byte
                   || value is short
                   || value is ushort
                   || value is int
                   || value is uint
                   || value is long
                   || value is ulong
                   || value is float
                   || value is double
                   || value is decimal;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Util/NumberUtilExtensions.cs`.

**Classes defined**: NumberExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 20
- Comment lines: 0
- Blank lines: 0

### Main Components

**Classes** (1):
- `NumberExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

