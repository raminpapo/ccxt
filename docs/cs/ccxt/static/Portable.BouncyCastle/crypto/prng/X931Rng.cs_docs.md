# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/prng/X931Rng.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/X931Rng.cs`
- **Size**: 6,196 bytes
- **Lines**: 203
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Crypto.Prng
{
    internal class X931Rng
    {
        private const long  BLOCK64_RESEED_MAX = 1L << (16 - 1);
        private const long  BLOCK128_RESEED_MAX = 1L << (24 - 1);
        private const int   BLOCK64_MAX_BITS_REQUEST = 1 << (13 - 1);
        private const int   BLOCK128_MAX_BITS_REQUEST = 1 << (19 - 1);

        private readonly IBlockCipher mEngine;
        private readonly IEntropySource mEntropySource;

        private readonly byte[] mDT;
        private readonly byte[] mI;
        private readonly byte[] mR;

        private byte[] mV;

        private long mReseedCounter = 1;

        /**
         *
         * @param engine
         * @param entropySource
         */
        internal X931Rng(IBlockCipher engine, byte[] dateTimeVector, IEntropySource entropySource)
        {
            this.mEngine = engine;
            this.mEntropySource = entropySource;

            this.mDT = new byte[engine.GetBlockSize()];

            Array.Copy(dateTimeVector, 0, mDT, 0, mDT.Length);

            this.mI = new byte[engine.GetBlockSize()];
            this.mR = new byte[engine.GetBlockSize()];
        }

        /**
         * Populate a passed in array with random data.
         *
         * @param output output array for generated bits.
         * @param predictionResistant true if a reseed should be forced, false otherwise.
         *
         * @return number of bits generated, -1 if a reseed required.
         */
        internal int Generate(byte[] output, int outputOff, int outputLen,  bool predictionResistant)
        {
            if (mR.Length == 8) // 64 bit block size
            {
                if (mReseedCounter > BLOCK64_RESEED_MAX)
                    return -1;

                if (outputLen > BLOCK64_MAX_BITS_REQUEST / 8)
                    throw new ArgumentException("Number of bits per request limited to " + BLOCK64_MAX_BITS_REQUEST, "output");
            }
            else
            {
                if (mReseedCounter > BLOCK128_RESEED_MAX)
                    return -1;

                if (outputLen > BLOCK128_MAX_BITS_REQUEST / 8)
                    throw new ArgumentException("Number of bits per request limited to " + BLOCK128_MAX_BITS_REQUEST, "output");
            }

            if (predictionResistant || mV == null)
            {
                mV = mEntropySource.GetEntropy();
                if (mV.Length != mEngine.GetBlockSize())
                    throw new InvalidOperationException("Insufficient entropy returned");
            }

            int m = outputLen / mR.Length;

            for (int i = 0; i < m; i++)
            {
                mEngine.ProcessBlock(mDT, 0, mI, 0);
                Process(mR, mI, mV);
                Process(mV, mR, mI);

                Array.Copy(mR, 0, output, outputOff + i * mR.Length, mR.Length);

                Increment(mDT);
            }

            int bytesToCopy = (outputLen - m * mR.Length);

            if (bytesToCopy > 0)
            {
                mEngine.ProcessBlock(mDT, 0, mI, 0);
                Process(mR, mI, mV);
                Process(mV, mR, mI);

                Array.Copy(mR, 0, output, outputOff + m * mR.Length, bytesToCopy);

                Increment(mDT);
            }

            mReseedCounter++;

            return outputLen * 8;
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        internal int Generate(Span<byte> output, bool predictionResistant)
        {
            int outputLen = output.Length;

            if (mR.Length == 8) // 64 bit block size
            {
                if (mReseedCounter > BLOCK64_RESEED_MAX)
                    return -1;

                if (outputLen > BLOCK64_MAX_BITS_REQUEST / 8)
                    throw new ArgumentException("Number of bits per request limited to " + BLOCK64_MAX_BITS_REQUEST, "output");
            }
            else
            {
                if (mReseedCounter > BLOCK128_RESEED_MAX)
                    return -1;

                if (outputLen > BLOCK128_MAX_BITS_REQUEST / 8)
                    throw new ArgumentException("Number of bits per request limited to " + BLOCK128_MAX_BITS_REQUEST, "output");
            }

            if (predictionResistant || mV == null)
            {
                mV = mEntropySource.GetEntropy();
                if (mV.Length != mEngine.GetBlockSize())
                    throw new InvalidOperationException("Insufficient entropy returned");
            }

            int m = outputLen / mR.Length;

            for (int i = 0; i < m; i++)
            {
                mEngine.ProcessBlock(mDT, 0, mI, 0);
                Process(mR, mI, mV);
                Process(mV, mR, mI);

                mR.CopyTo(output[(i * mR.Length)..]);

                Increment(mDT);
            }

            int bytesToCopy = (outputLen - m * mR.Length);

            if (bytesToCopy > 0)
            {
                mEngine.ProcessBlock(mDT, 0, mI, 0);
                Process(mR, mI, mV);
                Process(mV, mR, mI);

                mR.AsSpan(0, bytesToCopy).CopyTo(output[(m * mR.Length)..]);

                Increment(mDT);
            }

            mReseedCounter++;

            return outputLen * 8;
        }
#endif

        /**
         * Reseed the RNG.
         */
        internal void Reseed()
        {
            mV = mEntropySource.GetEntropy();
            if (mV.Length != mEngine.GetBlockSize())
                throw new InvalidOperationException("Insufficient entropy returned");
            mReseedCounter = 1;
        }

        internal IEntropySource EntropySource
        {
            get { return mEntropySource; }
        }

        private void Process(byte[] res, byte[] a, byte[] b)
        {
            for (int i = 0; i != res.Length; i++)
            {
                res[i] = (byte)(a[i] ^ b[i]);
            }

            mEngine.ProcessBlock(res, 0, res, 0);
        }

        private void Increment(byte[] val)
        {
            for (int i = val.Length - 1; i >= 0; i--)
            {
                if (++val[i] != 0)
                    break;
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/X931Rng.cs`.

**Classes defined**: X931Rng

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 203
- Code lines: 157
- Comment lines: 18
- Blank lines: 28

### Main Components

**Classes** (1):
- `X931Rng`

**Constants** (4):
- `BLOCK128_MAX_BITS_REQUEST`
- `BLOCK128_RESEED_MAX`
- `BLOCK64_MAX_BITS_REQUEST`
- `BLOCK64_RESEED_MAX`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

