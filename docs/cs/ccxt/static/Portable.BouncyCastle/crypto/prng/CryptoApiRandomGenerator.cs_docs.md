# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/prng/CryptoApiRandomGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/CryptoApiRandomGenerator.cs`
- **Size**: 1,936 bytes
- **Lines**: 74
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Security.Cryptography;

namespace Org.BouncyCastle.Crypto.Prng
{
    /// <summary>
    /// Uses RandomNumberGenerator.Create() to get randomness generator
    /// </summary>
    public class CryptoApiRandomGenerator
        : IRandomGenerator
    {
        private readonly RandomNumberGenerator rndProv;

        public CryptoApiRandomGenerator()
            : this(RandomNumberGenerator.Create())
        {
        }

        public CryptoApiRandomGenerator(RandomNumberGenerator rng)
        {
            this.rndProv = rng;
        }

        #region IRandomGenerator Members

        public virtual void AddSeedMaterial(byte[] seed)
        {
            // We don't care about the seed
        }

        public virtual void AddSeedMaterial(long seed)
        {
            // We don't care about the seed
        }

        public virtual void NextBytes(byte[] bytes)
        {
            rndProv.GetBytes(bytes);
        }

        public virtual void NextBytes(byte[] bytes, int start, int len)
        {
            if (start < 0)
                throw new ArgumentException("Start offset cannot be negative", "start");
            if (bytes.Length < (start + len))
                throw new ArgumentException("Byte array too small for requested offset and length");

#if NETCOREAPP2_0_OR_GREATER || NETSTANDARD2_0_OR_GREATER
            rndProv.GetBytes(bytes, start, len);
#else
            if (bytes.Length == len && start == 0) 
            {
                NextBytes(bytes);
            }
            else 
            {
                byte[] tmpBuf = new byte[len];
                NextBytes(tmpBuf);
                Array.Copy(tmpBuf, 0, bytes, start, len);
            }
#endif
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public virtual void NextBytes(Span<byte> bytes)
        {
            rndProv.GetBytes(bytes);
        }
#endif

#endregion
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/CryptoApiRandomGenerator.cs`.

**Classes defined**: CryptoApiRandomGenerator



## Detailed Walkthrough

### Code Structure

- Total lines: 74
- Code lines: 50
- Comment lines: 12
- Blank lines: 12

### Main Components

**Classes** (1):
- `CryptoApiRandomGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

