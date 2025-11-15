# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/operators/DefaultSignatureCalculator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/operators/DefaultSignatureCalculator.cs`
- **Size**: 597 bytes
- **Lines**: 29
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.IO;

using Org.BouncyCastle.Crypto.IO;

namespace Org.BouncyCastle.Crypto.Operators
{
    public class DefaultSignatureCalculator
        : IStreamCalculator
    {
        private readonly SignerSink mSignerSink;

        public DefaultSignatureCalculator(ISigner signer)
        {
            this.mSignerSink = new SignerSink(signer);
        }

        public Stream Stream
        {
            get { return mSignerSink; }
        }

        public object GetResult()
        {
            return new DefaultSignatureResult(mSignerSink.Signer);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/operators/DefaultSignatureCalculator.cs`.

**Classes defined**: DefaultSignatureCalculator



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 23
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `DefaultSignatureCalculator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

