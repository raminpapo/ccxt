# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DSAParameterGenerationParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DSAParameterGenerationParameters.cs`
- **Size**: 2,232 bytes
- **Lines**: 75
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class DsaParameterGenerationParameters
    {
        public const int DigitalSignatureUsage = 1;
        public const int KeyEstablishmentUsage = 2;

        private readonly int l;
        private readonly int n;
        private readonly int certainty;
        private readonly SecureRandom random;
        private readonly int usageIndex;

        /**
         * Construct without a usage index, this will do a random construction of G.
         *
         * @param L desired length of prime P in bits (the effective key size).
         * @param N desired length of prime Q in bits.
         * @param certainty certainty level for prime number generation.
         * @param random the source of randomness to use.
         */
        public DsaParameterGenerationParameters(int L, int N, int certainty, SecureRandom random)
            : this(L, N, certainty, random, -1)
        {
        }

        /**
         * Construct for a specific usage index - this has the effect of using verifiable canonical generation of G.
         *
         * @param L desired length of prime P in bits (the effective key size).
         * @param N desired length of prime Q in bits.
         * @param certainty certainty level for prime number generation.
         * @param random the source of randomness to use.
         * @param usageIndex a valid usage index.
         */
        public DsaParameterGenerationParameters(int L, int N, int certainty, SecureRandom random, int usageIndex)
        {
            this.l = L;
            this.n = N;
            this.certainty = certainty;
            this.random = random;
            this.usageIndex = usageIndex;
        }

        public virtual int L
        {
            get { return l; }
        }

        public virtual int N
        {
            get { return n; }
        }

        public virtual int UsageIndex
        {
            get { return usageIndex; }
        }

        public virtual int Certainty
        {
            get { return certainty; }
        }

        public virtual SecureRandom Random
        {
            get { return random; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DSAParameterGenerationParameters.cs`.

**Classes defined**: DsaParameterGenerationParameters

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 64
- Comment lines: 17
- Blank lines: -6

### Main Components

**Classes** (1):
- `DsaParameterGenerationParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

