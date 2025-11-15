# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/IesParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/IesParameters.cs`
- **Size**: 1,118 bytes
- **Lines**: 50
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Org.BouncyCastle.Crypto;

namespace Org.BouncyCastle.Crypto.Parameters
{
    /**
     * parameters for using an integrated cipher in stream mode.
     */
    public class IesParameters : ICipherParameters
    {
        private byte[]  derivation;
        private byte[]  encoding;
        private int     macKeySize;

        /**
         * @param derivation the derivation parameter for the KDF function.
         * @param encoding the encoding parameter for the KDF function.
         * @param macKeySize the size of the MAC key (in bits).
         */
        public IesParameters(
            byte[]  derivation,
            byte[]  encoding,
            int     macKeySize)
        {
            this.derivation = derivation;
            this.encoding = encoding;
            this.macKeySize = macKeySize;
        }

        public byte[] GetDerivationV()
        {
            return derivation;
        }

        public byte[] GetEncodingV()
        {
            return encoding;
        }

        public int MacKeySize
        {
			get
			{
				return macKeySize;
			}
        }
    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/IesParameters.cs`.

**Classes defined**: IesParameters

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 43
- Comment lines: 8
- Blank lines: -1

### Main Components

**Classes** (1):
- `IesParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

