# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/shape.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/shape.cs`
- **Size**: 1,174 bytes
- **Lines**: 53
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;
using System.Linq;

namespace StarknetSharp.Abi
{
    public class AbiDict
    {
        public AbiDict(List<AbiDictEntry> entries)
        {
            Entries = entries;
        }

        public List<AbiDictEntry> Entries { get; set; }
    }

    public abstract class AbiDictEntry
    {
        public string Type { get; set; }
    }

    public class FunctionDict : AbiDictEntry
    {
        public string Name { get; set; }
        public List<ParameterDict> Inputs { get; set; }
        public List<ParameterDict> Outputs { get; set; }
        public StateMutability? StateMutability { get; set; }
    }

    public abstract class ParameterDict
    {
        public string Name { get; set; }
        public string Type { get; set; }
    }

    public class StructMemberDict : ParameterDict
    {
        public int? Offset { get; set; }
    }

    public class StructDict : AbiDictEntry
    {
        public string Name { get; set; }
        public int Size { get; set; }
        public List<StructMemberDict> Members { get; set; }
    }

    public enum StateMutability
    {
        View,
        NonView
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.ABI/V1/shape.cs`.

**Classes defined**: AbiDict, StructDict, ParameterDict, StructMemberDict, AbiDictEntry, FunctionDict



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 45
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (6):
- `AbiDict`
- `AbiDictEntry`
- `FunctionDict`
- `ParameterDict`
- `StructDict`
- `StructMemberDict`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

