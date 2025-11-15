# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/prng/CryptoApiEntropySourceProvider.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/CryptoApiEntropySourceProvider.cs`
- **Size**: 1,955 bytes
- **Lines**: 68
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Security.Cryptography;

namespace Org.BouncyCastle.Crypto.Prng
{
    public class CryptoApiEntropySourceProvider
        :   IEntropySourceProvider
    {
        private readonly RandomNumberGenerator mRng;
        private readonly bool mPredictionResistant;

        public CryptoApiEntropySourceProvider()
            : this(RandomNumberGenerator.Create(), true)
        {
        }

        public CryptoApiEntropySourceProvider(RandomNumberGenerator rng, bool isPredictionResistant)
        {
            if (rng == null)
                throw new ArgumentNullException("rng");

            mRng = rng;
            mPredictionResistant = isPredictionResistant;
        }

        public IEntropySource Get(int bitsRequired)
        {
            return new CryptoApiEntropySource(mRng, mPredictionResistant, bitsRequired);
        }

        private class CryptoApiEntropySource
            :   IEntropySource
        {
            private readonly RandomNumberGenerator mRng;
            private readonly bool mPredictionResistant;
            private readonly int mEntropySize;

            internal CryptoApiEntropySource(RandomNumberGenerator rng, bool predictionResistant, int entropySize)
            {
                this.mRng = rng;
                this.mPredictionResistant = predictionResistant;
                this.mEntropySize = entropySize;
            }

            #region IEntropySource Members

            bool IEntropySource.IsPredictionResistant
            {
                get { return mPredictionResistant; }
            }

            byte[] IEntropySource.GetEntropy()
            {
                byte[] result = new byte[(mEntropySize + 7) / 8];
                mRng.GetBytes(result);
                return result;
            }

            int IEntropySource.EntropySize
            {
                get { return mEntropySize; }
            }

            #endregion
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/CryptoApiEntropySourceProvider.cs`.

**Classes defined**: CryptoApiEntropySourceProvider, CryptoApiEntropySource



## Detailed Walkthrough

### Code Structure

- Total lines: 68
- Code lines: 53
- Comment lines: 2
- Blank lines: 13

### Main Components

**Classes** (2):
- `CryptoApiEntropySource`
- `CryptoApiEntropySourceProvider`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

