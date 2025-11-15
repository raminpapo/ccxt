# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/field/GenericPolynomialExtensionField.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/field/GenericPolynomialExtensionField.cs`
- **Size**: 1,697 bytes
- **Lines**: 64
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Math.Field
{
    internal class GenericPolynomialExtensionField
        : IPolynomialExtensionField
    {
        protected readonly IFiniteField subfield;
        protected readonly IPolynomial minimalPolynomial;

        internal GenericPolynomialExtensionField(IFiniteField subfield, IPolynomial polynomial)
        {
            this.subfield = subfield;
            this.minimalPolynomial = polynomial;
        }

        public virtual BigInteger Characteristic
        {
            get { return subfield.Characteristic; }
        }

        public virtual int Dimension
        {
            get { return subfield.Dimension * minimalPolynomial.Degree; }
        }

        public virtual IFiniteField Subfield
        {
            get { return subfield; }
        }

        public virtual int Degree
        {
            get { return minimalPolynomial.Degree; }
        }

        public virtual IPolynomial MinimalPolynomial
        {
            get { return minimalPolynomial; }
        }

        public override bool Equals(object obj)
        {
            if (this == obj)
            {
                return true;
            }
            GenericPolynomialExtensionField other = obj as GenericPolynomialExtensionField;
            if (null == other)
            {
                return false;
            }
            return subfield.Equals(other.subfield) && minimalPolynomial.Equals(other.minimalPolynomial);
        }

        public override int GetHashCode()
        {
            return subfield.GetHashCode() ^ Integers.RotateLeft(minimalPolynomial.GetHashCode(), 16);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/field/GenericPolynomialExtensionField.cs`.

**Classes defined**: GenericPolynomialExtensionField



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 53
- Comment lines: 0
- Blank lines: 11

### Main Components

**Classes** (1):
- `GenericPolynomialExtensionField`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

