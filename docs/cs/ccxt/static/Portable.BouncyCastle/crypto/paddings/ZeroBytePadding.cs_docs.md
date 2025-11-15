# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/paddings/ZeroBytePadding.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/paddings/ZeroBytePadding.cs`
- **Size**: 2,214 bytes
- **Lines**: 83
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto.Paddings
{

    /// <summary> A padder that adds Null byte padding to a block.</summary>
    public class ZeroBytePadding : IBlockCipherPadding
    {
        /// <summary> Return the name of the algorithm the cipher implements.
        ///
        /// </summary>
        /// <returns> the name of the algorithm the cipher implements.
        /// </returns>
        public string PaddingName
        {
            get { return "ZeroBytePadding"; }
        }

		/// <summary> Initialise the padder.
        ///
        /// </summary>
        /// <param name="random">- a SecureRandom if available.
        /// </param>
        public void Init(SecureRandom random)
        {
            // nothing to do.
        }

        public int AddPadding(byte[] input, int inOff)
        {
            int added = input.Length - inOff;

            while (inOff < input.Length)
            {
                input[inOff++] = 0x00;
            }

            return added;
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public int AddPadding(Span<byte> block, int position)
        {
            int count = block.Length - position;
            block[position..].Fill(0x00);
            return count;
        }
#endif

        public int PadCount(byte[] input)
        {
            int count = 0, still00Mask = -1;
            int i = input.Length;
            while (--i >= 0)
            {
                int next = input[i];
                int match00Mask = ((next ^ 0x00) - 1) >> 31;
                still00Mask &= match00Mask;
                count -= still00Mask;
            }
            return count;
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public int PadCount(ReadOnlySpan<byte> block)
        {
            int count = 0, still00Mask = -1;
            int i = block.Length;
            while (--i >= 0)
            {
                int next = block[i];
                int match00Mask = ((next ^ 0x00) - 1) >> 31;
                still00Mask &= match00Mask;
                count -= still00Mask;
            }
            return count;
        }
#endif
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/paddings/ZeroBytePadding.cs`.

**Classes defined**: ZeroBytePadding



## Detailed Walkthrough

### Code Structure

- Total lines: 83
- Code lines: 56
- Comment lines: 16
- Blank lines: 11

### Main Components

**Classes** (1):
- `ZeroBytePadding`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

