# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/field/GF2Polynomial.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/field/GF2Polynomial.cs`
- **Size**: 1,037 bytes
- **Lines**: 47
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Math.Field
{
    internal class GF2Polynomial
        : IPolynomial
    {
        protected readonly int[] exponents;

        internal GF2Polynomial(int[] exponents)
        {
            this.exponents = Arrays.Clone(exponents);
        }

        public virtual int Degree
        {
            get { return exponents[exponents.Length - 1]; }
        }

        public virtual int[] GetExponentsPresent()
        {
            return Arrays.Clone(exponents);
        }

        public override bool Equals(object obj)
        {
            if (this == obj)
            {
                return true;
            }
            GF2Polynomial other = obj as GF2Polynomial;
            if (null == other)
            {
                return false;
            }
            return Arrays.AreEqual(exponents, other.exponents);
        }

        public override int GetHashCode()
        {
            return Arrays.GetHashCode(exponents);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/field/GF2Polynomial.cs`.

**Classes defined**: GF2Polynomial



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 39
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (1):
- `GF2Polynomial`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

