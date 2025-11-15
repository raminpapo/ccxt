# Documentation: cs/ccxt/static/Portable.BouncyCastle/security/SecurityUtilityException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/security/SecurityUtilityException.cs`
- **Size**: 550 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Security
{
    [Serializable]
    public class SecurityUtilityException
		: Exception
    {
		public SecurityUtilityException()
			: base()
		{
		}

		public SecurityUtilityException(string message)
			: base(message)
		{
		}

		public SecurityUtilityException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected SecurityUtilityException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/security/SecurityUtilityException.cs`.

**Classes defined**: SecurityUtilityException



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 26
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `SecurityUtilityException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

