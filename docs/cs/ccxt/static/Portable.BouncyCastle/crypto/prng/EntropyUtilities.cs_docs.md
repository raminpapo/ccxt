# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/prng/EntropyUtilities.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/EntropyUtilities.cs`
- **Size**: 981 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto.Prng
{
    public abstract class EntropyUtilities
    {
        /**
         * Generate numBytes worth of entropy from the passed in entropy source.
         *
         * @param entropySource the entropy source to request the data from.
         * @param numBytes the number of bytes of entropy requested.
         * @return a byte array populated with the random data.
         */
        public static byte[] GenerateSeed(IEntropySource entropySource, int numBytes)
        {
            byte[] bytes = new byte[numBytes];
            int count = 0;
            while (count < numBytes)
            {
                byte[] entropy = entropySource.GetEntropy();
                int toCopy = System.Math.Min(bytes.Length, numBytes - count);
                Array.Copy(entropy, 0, bytes, count, toCopy);
                count += toCopy;
            }
            return bytes;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/EntropyUtilities.cs`.

**Classes defined**: EntropyUtilities

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 28
- Comment lines: 7
- Blank lines: -4

### Main Components

**Classes** (1):
- `EntropyUtilities`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

