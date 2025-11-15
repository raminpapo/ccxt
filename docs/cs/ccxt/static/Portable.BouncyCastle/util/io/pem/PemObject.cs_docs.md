# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/pem/PemObject.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/pem/PemObject.cs`
- **Size**: 767 bytes
- **Lines**: 46
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Collections.Generic;

namespace Org.BouncyCastle.Utilities.IO.Pem
{
	public class PemObject
		: PemObjectGenerator
	{
		private string type;
		private IList<PemHeader> headers;
		private byte[] content;

		public PemObject(string type, byte[] content)
			: this(type, new List<PemHeader>(), content)
		{
		}

		public PemObject(string type, IList<PemHeader> headers, byte[] content)
		{
			this.type = type;
            this.headers = new List<PemHeader>(headers);
			this.content = content;
		}

		public string Type
		{
			get { return type; }
		}

		public IList<PemHeader> Headers
		{
			get { return headers; }
		}

		public byte[] Content
		{
			get { return content; }
		}

		public PemObject Generate()
		{
			return this;
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/pem/PemObject.cs`.

**Classes defined**: PemObject



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 38
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (1):
- `PemObject`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

