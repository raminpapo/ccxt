# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/edec/EdECObjectIdentifiers.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/edec/EdECObjectIdentifiers.cs`
- **Size**: 705 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1.EdEC
{
    /**
     * Edwards Elliptic Curve Object Identifiers (RFC 8410)
     */
    public abstract class EdECObjectIdentifiers
    {
        public static readonly DerObjectIdentifier id_edwards_curve_algs = new DerObjectIdentifier("1.3.101");

        public static readonly DerObjectIdentifier id_X25519 = id_edwards_curve_algs.Branch("110");
        public static readonly DerObjectIdentifier id_X448 = id_edwards_curve_algs.Branch("111");
        public static readonly DerObjectIdentifier id_Ed25519 = id_edwards_curve_algs.Branch("112");
        public static readonly DerObjectIdentifier id_Ed448 = id_edwards_curve_algs.Branch("113");
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/edec/EdECObjectIdentifiers.cs`.

**Classes defined**: EdECObjectIdentifiers

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 3
- Blank lines: 0

### Main Components

**Classes** (1):
- `EdECObjectIdentifiers`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

