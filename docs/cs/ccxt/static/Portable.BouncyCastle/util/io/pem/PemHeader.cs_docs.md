# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/pem/PemHeader.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/pem/PemHeader.cs`
- **Size**: 940 bytes
- **Lines**: 61
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Utilities.IO.Pem
{
	public class PemHeader
	{
		private string name;
		private string val;

		public PemHeader(string name, string val)
		{
			this.name = name;
			this.val = val;
		}

		public virtual string Name
		{
			get { return name; }
		}

		public virtual string Value
		{
			get { return val; }
		}

		public override int GetHashCode()
		{
			return GetHashCode(this.name) + 31 * GetHashCode(this.val);
		}

		public override bool Equals(object obj)
		{
			if (obj == this)
				return true;

			if (!(obj is PemHeader))
				return false;

			PemHeader other = (PemHeader)obj;

			return Platform.Equals(this.name, other.name)
				&& Platform.Equals(this.val, other.val);
		}

		private int GetHashCode(string s)
		{
			if (s == null)
			{
				return 1;
			}

			return s.GetHashCode();
		}

        public override string ToString()
        {
			return name + ":" + val;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/pem/PemHeader.cs`.

**Classes defined**: PemHeader



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 48
- Comment lines: 0
- Blank lines: 13

### Main Components

**Classes** (1):
- `PemHeader`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

