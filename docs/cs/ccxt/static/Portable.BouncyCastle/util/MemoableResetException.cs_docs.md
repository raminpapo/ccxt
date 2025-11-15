# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/MemoableResetException.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/MemoableResetException.cs`
- **Size**: 839 bytes
- **Lines**: 39
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Runtime.Serialization;

namespace Org.BouncyCastle.Utilities
{
	/**
     * Exception to be thrown on a failure to reset an object implementing Memoable.
     * <p>
     * The exception extends InvalidCastException to enable users to have a single handling case,
     * only introducing specific handling of this one if required.
     * </p>
     */
	[Serializable]
	public class MemoableResetException
        : InvalidCastException
    {
		public MemoableResetException()
			: base()
		{
		}

		public MemoableResetException(string message)
			: base(message)
		{
		}

		public MemoableResetException(string message, Exception innerException)
			: base(message, innerException)
		{
		}

		protected MemoableResetException(SerializationInfo info, StreamingContext context)
			: base(info, context)
		{
		}
	}
}


```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/MemoableResetException.cs`.

**Classes defined**: MemoableResetException

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 33
- Comment lines: 7
- Blank lines: -1

### Main Components

**Classes** (1):
- `MemoableResetException`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

