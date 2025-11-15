# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Tag.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Tag.cs`
- **Size**: 621 bytes
- **Lines**: 32
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    internal sealed class Asn1Tag
    {
        internal static Asn1Tag Create(int tagClass, int tagNo)
        {
            return new Asn1Tag(tagClass, tagNo);
        }

        private readonly int m_tagClass;
        private readonly int m_tagNo;

        private Asn1Tag(int tagClass, int tagNo)
        {
            m_tagClass = tagClass;
            m_tagNo = tagNo;
        }

        internal int TagClass
        {
            get { return m_tagClass; }
        }

        internal int TagNo
        {
            get { return m_tagNo; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Tag.cs`.

**Classes defined**: Asn1Tag



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 26
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `Asn1Tag`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

