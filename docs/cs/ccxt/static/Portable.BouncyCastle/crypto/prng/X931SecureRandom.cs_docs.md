# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/prng/X931SecureRandom.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/X931SecureRandom.cs`
- **Size**: 2,346 bytes
- **Lines**: 84
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto.Prng
{
    public class X931SecureRandom
        :   SecureRandom
    {
        private readonly bool           mPredictionResistant;
        private readonly SecureRandom   mRandomSource;
        private readonly X931Rng        mDrbg;

        internal X931SecureRandom(SecureRandom randomSource, X931Rng drbg, bool predictionResistant)
            : base(null)
        {
            this.mRandomSource = randomSource;
            this.mDrbg = drbg;
            this.mPredictionResistant = predictionResistant;
        }

        public override void SetSeed(byte[] seed)
        {
            lock (this)
            {
                if (mRandomSource != null)
                {
                    this.mRandomSource.SetSeed(seed);
                }
            }
        }

        public override void SetSeed(long seed)
        {
            lock (this)
            {
                // this will happen when SecureRandom() is created
                if (mRandomSource != null)
                {
                    this.mRandomSource.SetSeed(seed);
                }
            }
        }

        public override void NextBytes(byte[] bytes)
        {
            NextBytes(bytes, 0, bytes.Length);
        }

        public override void NextBytes(byte[] buf, int off, int len)
        {
            lock (this)
            {
                // check if a reseed is required...
                if (mDrbg.Generate(buf, off, len, mPredictionResistant) < 0)
                {
                    mDrbg.Reseed();
                    mDrbg.Generate(buf, off, len, mPredictionResistant);
                }
            }
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override void NextBytes(Span<byte> buffer)
        {
            lock (this)
            {
                // check if a reseed is required...
                if (mDrbg.Generate(buffer, mPredictionResistant) < 0)
                {
                    mDrbg.Reseed();
                    mDrbg.Generate(buffer, mPredictionResistant);
                }
            }
        }
#endif

        public override byte[] GenerateSeed(int numBytes)
        {
            return EntropyUtilities.GenerateSeed(mDrbg.EntropySource, numBytes);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/X931SecureRandom.cs`.

**Classes defined**: X931SecureRandom



## Detailed Walkthrough

### Code Structure

- Total lines: 84
- Code lines: 69
- Comment lines: 5
- Blank lines: 10

### Main Components

**Classes** (1):
- `X931SecureRandom`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

