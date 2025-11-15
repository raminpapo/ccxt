# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Type.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Type.cs`
- **Size**: 577 bytes
- **Lines**: 30
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Asn1
{
    internal abstract class Asn1Type
    {
        internal readonly Type m_platformType;

        internal Asn1Type(Type platformType)
        {
            m_platformType = platformType;
        }

        internal Type PlatformType
        {
            get { return m_platformType; }
        }

        public sealed override bool Equals(object that)
        {
            return this == that;
        }

        public sealed override int GetHashCode()
        {
            return base.GetHashCode();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/Asn1Type.cs`.

**Classes defined**: Asn1Type



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 24
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `Asn1Type`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

