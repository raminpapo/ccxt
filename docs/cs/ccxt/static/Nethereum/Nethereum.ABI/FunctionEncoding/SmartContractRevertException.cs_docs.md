# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/SmartContractRevertException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/SmartContractRevertException.cs`
- **Size**: 567 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Nethereum.ABI.FunctionEncoding
{
    public class SmartContractRevertException : Exception
    {
        private const string ERROR_PREFIX = "Smart contract error: ";
        public string RevertMessage { get; set;}
        public string EncodedData { get; set; }
        public SmartContractRevertException(string message, string encodedData, Exception innerException = null) : base(ERROR_PREFIX + message, innerException)
        {
            this.RevertMessage = message;
            this.EncodedData = encodedData;
        }
    }

   
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/SmartContractRevertException.cs`.

**Classes defined**: SmartContractRevertException



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `SmartContractRevertException`

**Constants** (1):
- `ERROR_PREFIX`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

