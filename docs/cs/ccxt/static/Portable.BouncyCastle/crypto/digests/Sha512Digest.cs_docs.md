# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/digests/Sha512Digest.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/digests/Sha512Digest.cs`
- **Size**: 3,132 bytes
- **Lines**: 124
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Crypto.Utilities;
using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Crypto.Digests
{
    /**
     * Draft FIPS 180-2 implementation of SHA-512. <b>Note:</b> As this is
     * based on a draft this implementation is subject to change.
     *
     * <pre>
     *         block  word  digest
     * SHA-1   512    32    160
     * SHA-256 512    32    256
     * SHA-384 1024   64    384
     * SHA-512 1024   64    512
     * </pre>
     */
    public class Sha512Digest
        : LongDigest
    {
        private const int DigestLength = 64;

        public Sha512Digest()
        {
        }

        /**
         * Copy constructor.  This will copy the state of the provided
         * message digest.
         */
        public Sha512Digest(
            Sha512Digest t)
            : base(t)
        {
        }

        public override string AlgorithmName
        {
            get { return "SHA-512"; }
        }

        public override int GetDigestSize()
        {
            return DigestLength;
        }

        public override int DoFinal(
            byte[]  output,
            int     outOff)
        {
            Finish();

            Pack.UInt64_To_BE(H1, output, outOff);
            Pack.UInt64_To_BE(H2, output, outOff + 8);
            Pack.UInt64_To_BE(H3, output, outOff + 16);
            Pack.UInt64_To_BE(H4, output, outOff + 24);
            Pack.UInt64_To_BE(H5, output, outOff + 32);
            Pack.UInt64_To_BE(H6, output, outOff + 40);
            Pack.UInt64_To_BE(H7, output, outOff + 48);
            Pack.UInt64_To_BE(H8, output, outOff + 56);

            Reset();

            return DigestLength;

        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override int DoFinal(Span<byte> output)
        {
            Finish();

            Pack.UInt64_To_BE(H1, output);
            Pack.UInt64_To_BE(H2, output[8..]);
            Pack.UInt64_To_BE(H3, output[16..]);
            Pack.UInt64_To_BE(H4, output[24..]);
            Pack.UInt64_To_BE(H5, output[32..]);
            Pack.UInt64_To_BE(H6, output[40..]);
            Pack.UInt64_To_BE(H7, output[48..]);
            Pack.UInt64_To_BE(H8, output[56..]);

            Reset();

            return DigestLength;
        }
#endif

        /**
        * reset the chaining variables
        */
        public override void Reset()
        {
            base.Reset();

            /* SHA-512 initial hash value
             * The first 64 bits of the fractional parts of the square roots
             * of the first eight prime numbers
             */
            H1 = 0x6a09e667f3bcc908;
            H2 = 0xbb67ae8584caa73b;
            H3 = 0x3c6ef372fe94f82b;
            H4 = 0xa54ff53a5f1d36f1;
            H5 = 0x510e527fade682d1;
            H6 = 0x9b05688c2b3e6c1f;
            H7 = 0x1f83d9abfb41bd6b;
            H8 = 0x5be0cd19137e2179;
        }
		
		public override IMemoable Copy()
		{
			return new Sha512Digest(this);
		}

		public override void Reset(IMemoable other)
		{
			Sha512Digest d = (Sha512Digest)other;

			CopyIn(d);
		}
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/digests/Sha512Digest.cs`.

**Classes defined**: Sha512Digest

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 124
- Code lines: 101
- Comment lines: 25
- Blank lines: -2

### Main Components

**Classes** (1):
- `Sha512Digest`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

