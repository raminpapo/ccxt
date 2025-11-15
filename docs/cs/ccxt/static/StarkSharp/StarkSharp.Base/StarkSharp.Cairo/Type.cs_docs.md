# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Cairo/Type.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Cairo/Type.cs`
- **Size**: 1,387 bytes
- **Lines**: 59
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿
using System.Collections.Generic;


namespace StarkSharp.Base.Cairo
{
    public abstract class CairoType { }
    public class FeltType : CairoType { }
    public class BoolType : CairoType { }
    public class TupleType : CairoType
    {
        public List<CairoType> Types { get; set; }
    }

    public class NamedTupleType : CairoType
    {
        public Dictionary<string, CairoType> Types { get; set; }
    }

    public class ArrayType : CairoType
    {
        public CairoType InnerType { get; set; }
    }

    public class StructType : CairoType
    {
        public string Name { get; set; }
        public Dictionary<string, CairoType> Types { get; set; }
    }
    public class EnumType : CairoType
    {
        public string Name { get; set; }
        public Dictionary<string, CairoType> Variants { get; set; }
    }
    public class OptionType : CairoType
    {
        public CairoType Type { get; set; }
    }
    public class UintType : CairoType
    {
        public int Bits { get; set; }

        public void CheckRange(int value)
        {
        }
    }

    public class TypeIdentifier : CairoType
    {
        public string Name { get; set; }
    }
    public class UnitType : CairoType { }
    public class EventType : CairoType
    {
        public string Name { get; set; }
        public Dictionary<string, CairoType> Types { get; set; }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Cairo/Type.cs`.

**Classes defined**: NamedTupleType, EnumType, ArrayType, OptionType, FeltType, UintType, StructType, BoolType, CairoType, TupleType



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 51
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (13):
- `ArrayType`
- `BoolType`
- `CairoType`
- `EnumType`
- `EventType`
- `FeltType`
- `NamedTupleType`
- `OptionType`
- `StructType`
- `TupleType`
- `TypeIdentifier`
- `UintType`
- `UnitType`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

