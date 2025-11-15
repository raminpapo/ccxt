# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/TupleTypeEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/TupleTypeEncoder.cs`
- **Size**: 882 bytes
- **Lines**: 33
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Nethereum.ABI.Encoders;
using Nethereum.ABI.FunctionEncoding;
using Nethereum.ABI.Model;

namespace Nethereum.ABI
{
    public class TupleTypeEncoder : ITypeEncoder
    {
        private readonly ParametersEncoder parametersEncoder;

        public TupleTypeEncoder()
        {
            parametersEncoder = new ParametersEncoder();
        }

        public Parameter[] Components { get; set; }

        public byte[] Encode(object value)
        {
            if (!(value == null || value is object[]))
                return parametersEncoder.EncodeParametersFromTypeAttributes(value.GetType(), value);

            var input = value as object[];
            return parametersEncoder.EncodeParameters(Components, input);
        }

        public byte[] EncodePacked(object value)
        {
            throw new NotImplementedException();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Encoders/TupleTypeEncoder.cs`.

**Classes defined**: TupleTypeEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 27
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `TupleTypeEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

