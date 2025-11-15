# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/ABIRepository/IABIInfoStorage.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/ABIRepository/IABIInfoStorage.cs`
- **Size**: 934 bytes
- **Lines**: 20
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.Model;
using System.Collections.Generic;
using System.Numerics;

namespace Nethereum.ABI.ABIRepository
{
    public interface IABIInfoStorage
    {
        void AddABIInfo(ABIInfo abiInfo);
        ErrorABI FindErrorABI(BigInteger chainId, string contractAddress, string signature);
        List<ErrorABI> FindErrorABI(string signature);
        EventABI FindEventABI(BigInteger chainId, string contractAddress, string signature);
        List<EventABI> FindEventABI(string signature);
        FunctionABI FindFunctionABI(BigInteger chainId, string contractAddress, string signature);
        List<FunctionABI> FindFunctionABI(string signature);
        FunctionABI FindFunctionABIFromInputData(BigInteger chainId, string contractAddress, string inputData);
        List<FunctionABI> FindFunctionABIFromInputData(string inputData);
        ABIInfo GetABIInfo(BigInteger chainId, string contractAddress);
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/ABIRepository/IABIInfoStorage.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 19
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

