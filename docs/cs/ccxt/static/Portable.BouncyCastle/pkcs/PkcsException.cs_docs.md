# Documentation: cs/ccxt/static/Portable.BouncyCastle/pkcs/PkcsException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/pkcs/PkcsException.cs`
- **Size**: 558 bytes
- **Lines**: 32
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Pkcs
{
	/// <summary>Base exception for PKCS related issues.</summary>
	[Serializable]
	public class PkcsException
        : Exception
    {
		public PkcsException()
			: base()
		{
		}

		public PkcsException(string message)
			: base(message)
		{
		}

		public PkcsException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected PkcsException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/pkcs/PkcsException.cs`.

**Classes defined**: PkcsException



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 26
- Comment lines: 1
- Blank lines: 5

### Main Components

**Classes** (1):
- `PkcsException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

