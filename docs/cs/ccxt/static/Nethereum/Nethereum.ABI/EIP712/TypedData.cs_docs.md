# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/TypedData.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/TypedData.cs`
- **Size**: 714 bytes
- **Lines**: 30
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Newtonsoft.Json;
using System.Collections.Generic;

namespace Nethereum.ABI.EIP712
{
    [JsonObject(MemberSerialization.OptIn)]
    public class TypedData<TDomain>: TypedDataRaw
    { 
        
        public TDomain Domain { get; set; }

        public void InitDomainRawValues()
        {
            DomainRawValues = MemberValueFactory.CreateFromMessage(Domain);
        }

        public void SetMessage<T>(T message)
        {
            Message = MemberValueFactory.CreateFromMessage(message);
        }

        public void EnsureDomainRawValuesAreInitialised()
        {
           if(DomainRawValues == null)
            {
                InitDomainRawValues();
            }
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/TypedData.cs`.

**Classes defined**: TypedData



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 25
- Comment lines: 0
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

