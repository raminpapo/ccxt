# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/MemberValue.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/MemberValue.cs`
- **Size**: 546 bytes
- **Lines**: 23
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿namespace Nethereum.ABI.EIP712
{

    public class MemberValue
    { 
        public string TypeName { get; set; }

        public object Value { get; set; }
    }

    public class Member
    {
        public Member() { }
        public Member(MemberDescription memberDescription, MemberValue memberValue)
        {
            MemberDescription = memberDescription;
            MemberValue = memberValue;
        }

        public MemberDescription MemberDescription { get; set; }
        public MemberValue MemberValue { get; set; }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/EIP712/MemberValue.cs`.

**Classes defined**: MemberValue, Member



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 19
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (2):
- `Member`
- `MemberValue`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

