# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/signers/IDsaKCalculator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/signers/IDsaKCalculator.cs`
- **Size**: 1,112 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Math;
using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto.Signers
{
    /**
     * Interface define calculators of K values for DSA/ECDSA.
     */
    public interface IDsaKCalculator
    {
        /**
         * Return true if this calculator is deterministic, false otherwise.
         *
         * @return true if deterministic, otherwise false.
         */
        bool IsDeterministic { get; }

        /**
         * Non-deterministic initialiser.
         *
         * @param n the order of the DSA group.
         * @param random a source of randomness.
         */
        void Init(BigInteger n, SecureRandom random);

        /**
         * Deterministic initialiser.
         *
         * @param n the order of the DSA group.
         * @param d the DSA private value.
         * @param message the message being signed.
         */
        void Init(BigInteger n, BigInteger d, byte[] message);

        /**
         * Return the next valid value of K.
         *
         * @return a K value.
         */
        BigInteger NextK();
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/signers/IDsaKCalculator.cs`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 39
- Comment lines: 26
- Blank lines: -20

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

