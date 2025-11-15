# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/StreamOverflowException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/StreamOverflowException.cs`
- **Size**: 565 bytes
- **Lines**: 32
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Utilities.IO
{
    [Serializable]
    public class StreamOverflowException
		: IOException
	{
		public StreamOverflowException()
			: base()
		{
		}

		public StreamOverflowException(string message)
			: base(message)
		{
		}

		public StreamOverflowException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected StreamOverflowException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/StreamOverflowException.cs`.

**Classes defined**: StreamOverflowException



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 27
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `StreamOverflowException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

