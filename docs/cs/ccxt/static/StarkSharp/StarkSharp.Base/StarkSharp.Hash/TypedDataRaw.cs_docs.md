# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Hash/TypedDataRaw.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Hash/TypedDataRaw.cs`
- **Size**: 435 bytes
- **Lines**: 15
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Newtonsoft.Json;
using System.Collections.Generic;

namespace StarkSharp.StarkSharp.Base.StarkSharp.Hash
{
    [JsonObject(MemberSerialization.OptIn)]
    public class TypedDataRaw
    {
        public IDictionary<string, MemberDescription[]> Types { get; set; }

        public string PrimaryType { get; set; }
        public MemberValue[] Message { get; set; }
        public MemberValue[] DomainRawValues { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Hash/TypedDataRaw.cs`.

**Classes defined**: TypedDataRaw



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 13
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `TypedDataRaw`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

