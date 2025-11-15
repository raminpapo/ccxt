# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/date/DateTimeObject.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/date/DateTimeObject.cs`
- **Size**: 327 bytes
- **Lines**: 26
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Utilities.Date
{
	public sealed class DateTimeObject
	{
		private readonly DateTime dt;

		public DateTimeObject(
			DateTime dt)
		{
			this.dt = dt;
		}

		public DateTime Value
		{
			get { return dt; }
		}

		public override string ToString()
		{
			return dt.ToString();
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/date/DateTimeObject.cs`.

**Classes defined**: DateTimeObject



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 21
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `DateTimeObject`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

