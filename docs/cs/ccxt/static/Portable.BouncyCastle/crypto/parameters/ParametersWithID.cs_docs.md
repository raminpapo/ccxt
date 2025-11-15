# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithID.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithID.cs`
- **Size**: 838 bytes
- **Lines**: 37
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class ParametersWithID
        : ICipherParameters
    {
        private readonly ICipherParameters parameters;
        private readonly byte[] id;

        public ParametersWithID(ICipherParameters parameters,
            byte[] id)
            : this(parameters, id, 0, id.Length)
        {
        }

        public ParametersWithID(ICipherParameters parameters,
            byte[] id, int idOff, int idLen)
        {
            this.parameters = parameters;
            this.id = Arrays.CopyOfRange(id, idOff, idOff + idLen);
        }

        public byte[] GetID()
        {
            return id;
        }

        public ICipherParameters Parameters
        {
            get { return parameters; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithID.cs`.

**Classes defined**: ParametersWithID



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 30
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `ParametersWithID`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

