# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/LazyASN1InputStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/LazyASN1InputStream.cs`
- **Size**: 1,138 bytes
- **Lines**: 44
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Asn1
{
    public class LazyAsn1InputStream
        : Asn1InputStream
    {
        public LazyAsn1InputStream(byte[] input)
            : base(input)
        {
        }

        public LazyAsn1InputStream(Stream inputStream)
            : base(inputStream)
        {
        }

        internal LazyAsn1InputStream(Stream input, int limit, byte[][] tmpBuffers)
            : base(input, limit, tmpBuffers)
        {
        }

        internal override Asn1Sequence CreateDLSequence(DefiniteLengthInputStream defIn)
        {
            return new LazyDLSequence(defIn.ToArray());
        }

        internal override Asn1Set CreateDLSet(DefiniteLengthInputStream defIn)
        {
            return new LazyDLSet(defIn.ToArray());
        }

        internal override Asn1EncodableVector ReadVector(DefiniteLengthInputStream defIn)
        {
            int remaining = defIn.Remaining;
            if (remaining < 1)
                return new Asn1EncodableVector(0);

            return new LazyAsn1InputStream(defIn, remaining, tmpBuffers).ReadVector();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/LazyASN1InputStream.cs`.

**Classes defined**: LazyAsn1InputStream



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 36
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (1):
- `LazyAsn1InputStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

