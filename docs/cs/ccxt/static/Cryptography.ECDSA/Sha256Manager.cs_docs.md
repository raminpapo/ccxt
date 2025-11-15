# Documentation: cs/ccxt/static/Cryptography.ECDSA/Sha256Manager.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Sha256Manager.cs`
- **Size**: 1,047 bytes
- **Lines**: 47
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using Cryptography.ECDSA.Internal.Sha256;

namespace Cryptography.ECDSA
{
    public class Sha256Manager
    {
        private readonly Sha256T _sha;

        public Sha256Manager()
        {
            _sha = new Sha256T();
            Hash.Initialize(_sha);
        }


        public void Write(byte[] data)
        {
            Hash.Write(_sha, data, (UInt32)data.Length);
        }

        public void Write(byte[] data, int len)
        {
            Hash.Write(_sha, data, (UInt32)len);
        }

        public byte[] FinalizeAndGetResult()
        {
            byte[] outputSer = new byte[32];
            Hash.Finalize(_sha, outputSer);
            return outputSer;
        }


        
        public static byte[] GetHash(byte[] data)
        {
            Sha256T sha = new Sha256T();
            Hash.Initialize(sha);
            Hash.Write(sha, data, (UInt32)data.Length);
            byte[] outputSer = new byte[32];
            Hash.Finalize(sha, outputSer);
            return outputSer;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Sha256Manager.cs`.

**Classes defined**: Sha256Manager



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 37
- Comment lines: 0
- Blank lines: 10

### Main Components

**Classes** (1):
- `Sha256Manager`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

