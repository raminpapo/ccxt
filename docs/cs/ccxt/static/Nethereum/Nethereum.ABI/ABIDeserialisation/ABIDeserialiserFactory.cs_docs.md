# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/ABIDeserialisation/ABIDeserialiserFactory.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/ABIDeserialisation/ABIDeserialiserFactory.cs`
- **Size**: 1,016 bytes
- **Lines**: 35
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.Model;
using System;


namespace Nethereum.ABI.ABIDeserialisation
{
    public class ABIDeserialiserFactory
    {
        public static ContractABI DeserialiseContractABI(string jsonOrStringSignatureABI)
        {
            try
            {
                if (IsJson(jsonOrStringSignatureABI))
                {
                    return new ABIJsonDeserialiser().DeserialiseContract(jsonOrStringSignatureABI);
                }

                return new ABIStringSignatureDeserialiser().ExtractContractABIWithLineBreakSplitSignatures(jsonOrStringSignatureABI);
            }
            catch(Exception ex)
            {
                throw new FormatException("Invalid ABI, could not be parsed", ex);
            }
            
        }

        private static bool IsJson(string value)
        {
            value = value.Trim();
            return value.StartsWith("{") && value.EndsWith("}")
                   || value.StartsWith("[") && value.EndsWith("]");
        }

    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/ABIDeserialisation/ABIDeserialiserFactory.cs`.

**Classes defined**: ABIDeserialiserFactory



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 29
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `ABIDeserialiserFactory`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

