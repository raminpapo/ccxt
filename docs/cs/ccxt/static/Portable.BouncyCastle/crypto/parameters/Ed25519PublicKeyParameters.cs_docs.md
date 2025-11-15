# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/Ed25519PublicKeyParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/Ed25519PublicKeyParameters.cs`
- **Size**: 1,389 bytes
- **Lines**: 54
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.IO;

using Org.BouncyCastle.Math.EC.Rfc8032;
using Org.BouncyCastle.Utilities;
using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public sealed class Ed25519PublicKeyParameters
        : AsymmetricKeyParameter
    {
        public static readonly int KeySize = Ed25519.PublicKeySize;

        private readonly byte[] data = new byte[KeySize];

        public Ed25519PublicKeyParameters(byte[] buf)
            : this(Validate(buf), 0)
        {
        }

        public Ed25519PublicKeyParameters(byte[] buf, int off)
            : base(false)
        {
            Array.Copy(buf, off, data, 0, KeySize);
        }

        public Ed25519PublicKeyParameters(Stream input)
            : base(false)
        {
            if (KeySize != Streams.ReadFully(input, data))
                throw new EndOfStreamException("EOF encountered in middle of Ed25519 public key");
        }

        public void Encode(byte[] buf, int off)
        {
            Array.Copy(data, 0, buf, off, KeySize);
        }

        public byte[] GetEncoded()
        {
            return Arrays.Clone(data);
        }

        private static byte[] Validate(byte[] buf)
        {
            if (buf.Length != KeySize)
                throw new ArgumentException("must have length " + KeySize, "buf");

            return buf;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/Ed25519PublicKeyParameters.cs`.

**Classes defined**: Ed25519PublicKeyParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 43
- Comment lines: 0
- Blank lines: 11

### Main Components

**Classes** (1):
- `Ed25519PublicKeyParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

