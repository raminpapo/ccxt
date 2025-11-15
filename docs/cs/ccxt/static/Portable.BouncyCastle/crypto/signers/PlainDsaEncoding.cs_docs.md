# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/signers/PlainDsaEncoding.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/signers/PlainDsaEncoding.cs`
- **Size**: 1,998 bytes
- **Lines**: 59
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Math;
using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Crypto.Signers
{
    public class PlainDsaEncoding
        : IDsaEncoding
    {
        public static readonly PlainDsaEncoding Instance = new PlainDsaEncoding();

        public virtual BigInteger[] Decode(BigInteger n, byte[] encoding)
        {
            int valueLength = BigIntegers.GetUnsignedByteLength(n);
            if (encoding.Length != valueLength * 2)
                throw new ArgumentException("Encoding has incorrect length", "encoding");

            return new BigInteger[] {
                DecodeValue(n, encoding, 0, valueLength),
                DecodeValue(n, encoding, valueLength, valueLength),
            };
        }

        public virtual byte[] Encode(BigInteger n, BigInteger r, BigInteger s)
        {
            int valueLength = BigIntegers.GetUnsignedByteLength(n);
            byte[] result = new byte[valueLength * 2];
            EncodeValue(n, r, result, 0, valueLength);
            EncodeValue(n, s, result, valueLength, valueLength);
            return result;
        }

        protected virtual BigInteger CheckValue(BigInteger n, BigInteger x)
        {
            if (x.SignValue < 0 || x.CompareTo(n) >= 0)
                throw new ArgumentException("Value out of range", "x");

            return x;
        }

        protected virtual BigInteger DecodeValue(BigInteger n, byte[] buf, int off, int len)
        {
            return CheckValue(n, new BigInteger(1, buf, off, len));
        }

        protected virtual void EncodeValue(BigInteger n, BigInteger x, byte[] buf, int off, int len)
        {
            byte[] bs = CheckValue(n, x).ToByteArrayUnsigned();
            int bsOff = System.Math.Max(0, bs.Length - len);
            int bsLen = bs.Length - bsOff;

            int pos = len - bsLen;
            Arrays.Fill(buf, off, off + pos, 0);
            Array.Copy(bs, bsOff, buf, off + pos, bsLen);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/signers/PlainDsaEncoding.cs`.

**Classes defined**: PlainDsaEncoding



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 48
- Comment lines: 0
- Blank lines: 11

### Main Components

**Classes** (1):
- `PlainDsaEncoding`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

