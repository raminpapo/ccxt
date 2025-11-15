# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/AbiEncodingException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/AbiEncodingException.cs`
- **Size**: 494 bytes
- **Lines**: 20
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Nethereum.ABI.FunctionEncoding
{
    public class AbiEncodingException:Exception
    {
        public AbiEncodingException(int order, ABIType abiType, object value, string message, Exception innerException):base(message, innerException)
        {
            Order = order;
            ABIType = abiType;
            Value = value;
        }

        public int Order { get;}
        public ABIType ABIType { get; }
        public object Value { get; }
    }
 }

   
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/AbiEncodingException.cs`.

**Classes defined**: AbiEncodingException



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 16
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `AbiEncodingException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

