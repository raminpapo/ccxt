# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/TypedDataRaw.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/TypedDataRaw.cs`
- **Size**: 516 bytes
- **Lines**: 17
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Newtonsoft.Json;
using System.Collections.Generic;

namespace Nethereum.ABI.EIP712
{
    [JsonObject(MemberSerialization.OptIn)]
    public class TypedDataRaw
    {
        [JsonProperty(PropertyName = "types")]
        public IDictionary<string, MemberDescription[]> Types { get; set; }

        [JsonProperty(PropertyName = "primaryType")]
        public string PrimaryType { get; set; }
        public MemberValue[] Message { get; set; }
        public MemberValue[] DomainRawValues { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/TypedDataRaw.cs`.

**Classes defined**: TypedDataRaw



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 15
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

