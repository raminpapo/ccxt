# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/TransactionUtils.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/TransactionUtils.cs`
- **Size**: 524 bytes
- **Lines**: 21
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Collections.Generic;
using System;

namespace Nethereum.Util
{
    public static class TransactionUtils
    {
        public static string CalculateTransactionHash(string rawSignedTransaction)
        {
            var sha3 = new Sha3Keccack();
            return sha3.CalculateHashFromHex(rawSignedTransaction);
        }
    }

    public class UniqueTransactionHashList : HashSet<string>
    {
        public UniqueTransactionHashList() : base(StringComparer.OrdinalIgnoreCase)
        {
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/TransactionUtils.cs`.

**Classes defined**: TransactionUtils, UniqueTransactionHashList



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 19
- Comment lines: 0
- Blank lines: 2

### Main Components

**Classes** (2):
- `TransactionUtils`
- `UniqueTransactionHashList`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

