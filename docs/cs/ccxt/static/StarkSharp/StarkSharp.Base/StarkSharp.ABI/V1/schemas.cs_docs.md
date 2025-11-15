# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/schemas.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/schemas.cs`
- **Size**: 899 bytes
- **Lines**: 39
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;
using System.Linq;

namespace StarknetSharp.Abi
{
    public class ContractAbiEntrySchema
    {
        public ContractAbiEntrySchema(AbiComponentSchema schema)
        {
            Schema = schema;
        }

        public AbiComponentSchema Schema { get; set; }
    }

    public abstract class AbiComponentSchema
    {
        public string Type { get; set; }
    }

    public class FunctionAbiEntrySchema : AbiComponentSchema
    {
        public string Name { get; set; }
        public List<ParameterSchema> Inputs { get; set; }
        public List<ParameterSchema> Outputs { get; set; }
    }

    public abstract class ParameterSchema
    {
        public string Name { get; set; }
        public string Type { get; set; }
    }

    public class StructMemberSchema : ParameterSchema
    {
        public int Offset { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/schemas.cs`.

**Classes defined**: FunctionAbiEntrySchema, AbiComponentSchema, StructMemberSchema, ParameterSchema, ContractAbiEntrySchema



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 33
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (5):
- `AbiComponentSchema`
- `ContractAbiEntrySchema`
- `FunctionAbiEntrySchema`
- `ParameterSchema`
- `StructMemberSchema`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

