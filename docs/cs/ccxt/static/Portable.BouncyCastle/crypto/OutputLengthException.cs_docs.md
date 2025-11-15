# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/OutputLengthException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/OutputLengthException.cs`
- **Size**: 552 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Crypto
{
    [Serializable]
    public class OutputLengthException
        : DataLengthException
    {
		public OutputLengthException()
			: base()
		{
		}

		public OutputLengthException(string message)
			: base(message)
		{
		}

		public OutputLengthException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected OutputLengthException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/OutputLengthException.cs`.

**Classes defined**: OutputLengthException



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 26
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `OutputLengthException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

