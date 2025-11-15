# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/Domain.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/Domain.cs`
- **Size**: 1,830 bytes
- **Lines**: 72
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.FunctionEncoding.Attributes;
using System.Numerics;

namespace Nethereum.ABI.EIP712
{
    //Interface placeholder for any domain type including any optional fields
    public interface IDomain
    {

    }

    [Struct("EIP712Domain")]
    public class DomainWithVerifyingContract : IDomain
    {

        [Parameter("address", "verifyingContract", 1)]
        public virtual string VerifyingContract { get; set; }

    }

    [Struct("EIP712Domain")]
    public class DomainWithNameVersionAndChainId: IDomain
    {
        [Parameter("string", "name", 1)]
        public virtual string Name { get; set; }

        [Parameter("string", "version", 2)]
        public virtual string Version { get; set; }

        [Parameter("uint256", "chainId", 3)]
        public virtual BigInteger? ChainId { get; set; }

    }



    [Struct("EIP712Domain")]
    public class DomainWithChainIdAndVerifyingContract : IDomain
    {
        [Parameter("uint256", "chainId", 1)]
        public virtual BigInteger? ChainId { get; set; }

        [Parameter("address", "verifyingContract", 2)]
        public virtual string VerifyingContract { get; set; }

    }


    [Struct("EIP712Domain")]
    public class Domain:IDomain
    {
        [Parameter("string", "name", 1)]
        public virtual string Name { get; set; }

        [Parameter("string", "version", 2)]
        public virtual string Version { get; set; }

        [Parameter("uint256", "chainId", 3)]
        public virtual BigInteger? ChainId { get; set; }

        [Parameter("address", "verifyingContract", 4)]
        public virtual string VerifyingContract { get; set; }
       
    }

    [Struct("EIP712Domain")]
    public class DomainWithSalt:Domain
    {
        [Parameter("bytes32", "salt", 5)]
        public virtual byte[] Salt { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/Domain.cs`.

**Classes defined**: DomainWithChainIdAndVerifyingContract, DomainWithSalt, DomainWithNameVersionAndChainId, DomainWithVerifyingContract, Domain



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 50
- Comment lines: 1
- Blank lines: 21

### Main Components

**Classes** (5):
- `Domain`
- `DomainWithChainIdAndVerifyingContract`
- `DomainWithNameVersionAndChainId`
- `DomainWithSalt`
- `DomainWithVerifyingContract`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

