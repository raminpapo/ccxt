# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Model/EventABI.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Model/EventABI.cs`
- **Size**: 1,289 bytes
- **Lines**: 50
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Nethereum.ABI.FunctionEncoding;
using System.Linq;

namespace Nethereum.ABI.Model
{
    public class EventABI
    {
        private readonly SignatureEncoder signatureEncoder;
        private string sha3Signature;
        private int? numberOfIndexes;

        public EventABI(string name) : this(name, false)
        {
        }

        public EventABI(string name, bool isAnonymous)
        {
            Name = name;
            IsAnonymous = isAnonymous;
            signatureEncoder = new SignatureEncoder();
        }

        public string Name { get; }
        public bool IsAnonymous { get; set; }

        public Parameter[] InputParameters { get; set; }

        public string Sha3Signature
        {
            get
            {
                if (sha3Signature != null) return sha3Signature;
                sha3Signature = signatureEncoder.GenerateSha3Signature(Name, InputParameters);
                return sha3Signature;
            }
        }

        public int NumberOfIndexes
        {
            get
            {
                if(numberOfIndexes == null)
                {
                    numberOfIndexes = InputParameters.Count(x => x.Indexed == true);
                }
                return numberOfIndexes.Value;
            }
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Model/EventABI.cs`.

**Classes defined**: EventABI



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 43
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `EventABI`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

