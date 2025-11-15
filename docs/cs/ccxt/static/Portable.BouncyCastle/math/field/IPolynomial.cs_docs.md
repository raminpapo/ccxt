# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/field/IPolynomial.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/field/IPolynomial.cs`
- **Size**: 251 bytes
- **Lines**: 16
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.Field
{
    public interface IPolynomial
    {
        int Degree { get; }

        //BigInteger[] GetCoefficients();

        int[] GetExponentsPresent();

        //Term[] GetNonZeroTerms();
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/field/IPolynomial.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 9
- Comment lines: 2
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

