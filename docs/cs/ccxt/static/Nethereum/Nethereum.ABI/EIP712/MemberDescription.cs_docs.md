# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/MemberDescription.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/MemberDescription.cs`
- **Size**: 472 bytes
- **Lines**: 20
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI;
using Nethereum.ABI.FunctionEncoding.Attributes;
using Nethereum.ABI.Model;
using Newtonsoft.Json;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Reflection;

namespace Nethereum.ABI.EIP712
{
    public class MemberDescription
    {
        [JsonProperty(PropertyName = "name")]
        public string Name { get; set; }

        [JsonProperty(PropertyName = "type")]
        public string Type { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/MemberDescription.cs`.

**Classes defined**: MemberDescription



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 18
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (1):
- `MemberDescription`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

