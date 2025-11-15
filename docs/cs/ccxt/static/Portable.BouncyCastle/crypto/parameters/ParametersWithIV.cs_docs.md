# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithIV.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithIV.cs`
- **Size**: 1,001 bytes
- **Lines**: 41
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class ParametersWithIV
        : ICipherParameters
    {
        private readonly ICipherParameters parameters;
        private readonly byte[] iv;

        public ParametersWithIV(ICipherParameters parameters,
            byte[] iv)
            : this(parameters, iv, 0, iv.Length)
        {
        }

        public ParametersWithIV(ICipherParameters parameters,
            byte[] iv, int ivOff, int ivLen)
        {
            // NOTE: 'parameters' may be null to imply key re-use
            if (iv == null)
                throw new ArgumentNullException("iv");

            this.parameters = parameters;
            this.iv = Arrays.CopyOfRange(iv, ivOff, ivOff + ivLen);
        }

        public byte[] GetIV()
        {
            return (byte[])iv.Clone();
        }

        public ICipherParameters Parameters
        {
            get { return parameters; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithIV.cs`.

**Classes defined**: ParametersWithIV



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 32
- Comment lines: 1
- Blank lines: 8

### Main Components

**Classes** (1):
- `ParametersWithIV`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

