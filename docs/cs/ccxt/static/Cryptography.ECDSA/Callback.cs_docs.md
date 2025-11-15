# Documentation: cs/ccxt/static/Cryptography.ECDSA/Callback.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Callback.cs`
- **Size**: 267 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Cryptography.ECDSA
{
    public class Callback : EventArgs
    {
        public Callback()
        {
        }

        public Callback(string message)
        {
            Message = message;
        }

        public string Message;
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Callback.cs`.

**Classes defined**: Callback



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `Callback`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

