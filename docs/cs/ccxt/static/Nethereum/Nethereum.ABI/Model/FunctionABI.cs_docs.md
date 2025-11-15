# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Model/FunctionABI.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Model/FunctionABI.cs`
- **Size**: 1,053 bytes
- **Lines**: 37
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.ABI.FunctionEncoding;

namespace Nethereum.ABI.Model
{
    public class FunctionABI
    {
        private readonly SignatureEncoder signatureEncoder;
        private string sha3Signature;

        public FunctionABI(string name, bool constant, bool serpent = false)
        {
            Name = name;
            Serpent = serpent;
            Constant = constant;
            signatureEncoder = serpent ? new SerpentSignatureEncoder() : new SignatureEncoder();
        }

        public bool Serpent { get; private set; }

        public bool Constant { get; private set; }

        public string Name { get; }

        public Parameter[] InputParameters { get; set; }
        public Parameter[] OutputParameters { get; set; }

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

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Model/FunctionABI.cs`.

**Classes defined**: FunctionABI



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 30
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `FunctionABI`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

