# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Model/ErrorABI.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Model/ErrorABI.cs`
- **Size**: 747 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.FunctionEncoding;

namespace Nethereum.ABI.Model
{
    public class ErrorABI
    {
        private readonly SignatureEncoder signatureEncoder;

        private string sha3Signature;

        public ErrorABI(string name)
        {
            Name = name;
            signatureEncoder = new SignatureEncoder();
        }

        public string Name { get; }
        public Parameter[] InputParameters { get; set; }

        public string Sha3Signature
        {
            get
            {
                if (sha3Signature != null) return sha3Signature;
                sha3Signature = signatureEncoder.GenerateSha3Signature(Name, InputParameters, 4);
                return sha3Signature;
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Model/ErrorABI.cs`.

**Classes defined**: ErrorABI



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 25
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `ErrorABI`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

