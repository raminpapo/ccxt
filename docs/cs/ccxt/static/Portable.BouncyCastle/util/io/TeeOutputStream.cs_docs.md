# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/TeeOutputStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/TeeOutputStream.cs`
- **Size**: 1,107 bytes
- **Lines**: 52
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Diagnostics;
using System.IO;

namespace Org.BouncyCastle.Utilities.IO
{
    public class TeeOutputStream
		: BaseOutputStream
	{
		private readonly Stream output, tee;

		public TeeOutputStream(Stream output, Stream tee)
		{
			Debug.Assert(output.CanWrite);
			Debug.Assert(tee.CanWrite);

			this.output = output;
			this.tee = tee;
		}

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                Platform.Dispose(output);
                Platform.Dispose(tee);
            }
            base.Dispose(disposing);
        }

        public override void Write(byte[] buffer, int offset, int count)
		{
			output.Write(buffer, offset, count);
			tee.Write(buffer, offset, count);
		}

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override void Write(ReadOnlySpan<byte> buffer)
        {
            output.Write(buffer);
            tee.Write(buffer);
        }
#endif

        public override void WriteByte(byte value)
		{
			output.WriteByte(value);
			tee.WriteByte(value);
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/TeeOutputStream.cs`.

**Classes defined**: TeeOutputStream



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 42
- Comment lines: 2
- Blank lines: 8

### Main Components

**Classes** (1):
- `TeeOutputStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

