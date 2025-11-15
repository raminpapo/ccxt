# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/TeeInputStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/TeeInputStream.cs`
- **Size**: 1,234 bytes
- **Lines**: 70
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Diagnostics;
using System.IO;

namespace Org.BouncyCastle.Utilities.IO
{
	public class TeeInputStream
		: BaseInputStream
	{
		private readonly Stream input, tee;

		public TeeInputStream(Stream input, Stream tee)
		{
			Debug.Assert(input.CanRead);
			Debug.Assert(tee.CanWrite);

			this.input = input;
			this.tee = tee;
		}

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                Platform.Dispose(input);
                Platform.Dispose(tee);
            }
            base.Dispose(disposing);
        }

        public override int Read(byte[] buffer, int offset, int count)
		{
			int i = input.Read(buffer, offset, count);

			if (i > 0)
			{
				tee.Write(buffer, offset, i);
			}

			return i;
		}

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override int Read(Span<byte> buffer)
        {
            int i = input.Read(buffer);

            if (i > 0)
            {
				tee.Write(buffer[..i]);
            }

            return i;
        }
#endif

        public override int ReadByte()
		{
			int i = input.ReadByte();

			if (i >= 0)
			{
				tee.WriteByte((byte)i);
			}

			return i;
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/TeeInputStream.cs`.

**Classes defined**: TeeInputStream



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 54
- Comment lines: 2
- Blank lines: 14

### Main Components

**Classes** (1):
- `TeeInputStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

