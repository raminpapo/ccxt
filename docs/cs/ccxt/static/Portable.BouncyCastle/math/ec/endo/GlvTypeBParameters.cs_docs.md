# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/GlvTypeBParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/GlvTypeBParameters.cs`
- **Size**: 784 bytes
- **Lines**: 33
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.EC.Endo
{
    public class GlvTypeBParameters
    {
        protected readonly BigInteger m_beta, m_lambda;
        protected readonly ScalarSplitParameters m_splitParams;

        public GlvTypeBParameters(BigInteger beta, BigInteger lambda, ScalarSplitParameters splitParams)
        {
            this.m_beta = beta;
            this.m_lambda = lambda;
            this.m_splitParams = splitParams;
        }

        public virtual BigInteger Beta
        {
            get { return m_beta; }
        }

        public virtual BigInteger Lambda
        {
            get { return m_lambda; }
        }

        public virtual ScalarSplitParameters SplitParams
        {
            get { return m_splitParams; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/GlvTypeBParameters.cs`.

**Classes defined**: GlvTypeBParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 27
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `GlvTypeBParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

