# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/ValidityPreCompInfo.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/ValidityPreCompInfo.cs`
- **Size**: 914 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.EC.Multiplier
{
    internal class ValidityPreCompInfo
        : PreCompInfo
    {
        internal static readonly string PRECOMP_NAME = "bc_validity";

        private bool failed = false;
        private bool curveEquationPassed = false;
        private bool orderPassed = false;

        internal bool HasFailed()
        {
            return failed;
        }

        internal void ReportFailed()
        {
            failed = true;
        }

        internal bool HasCurveEquationPassed()
        {
            return curveEquationPassed;
        }

        internal void ReportCurveEquationPassed()
        {
            curveEquationPassed = true;
        }

        internal bool HasOrderPassed()
        {
            return orderPassed;
        }

        internal void ReportOrderPassed()
        {
            orderPassed = true;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/ValidityPreCompInfo.cs`.

**Classes defined**: ValidityPreCompInfo



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 36
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `ValidityPreCompInfo`

**Constants** (1):
- `PRECOMP_NAME`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

