# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/PushbackStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/PushbackStream.cs`
- **Size**: 1,527 bytes
- **Lines**: 84
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Utilities.IO
{
	public class PushbackStream
		: FilterStream
	{
		private int m_buf = -1;

		public PushbackStream(Stream s)
			: base(s)
		{
		}

#if NETCOREAPP2_0_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override void CopyTo(Stream destination, int bufferSize)
        {
			if (m_buf != -1)
			{
				destination.WriteByte((byte)m_buf);
                m_buf = -1;
            }

            s.CopyTo(destination, bufferSize);
        }
#endif

        public override int Read(byte[] buffer, int offset, int count)
		{
			Streams.ValidateBufferArguments(buffer, offset, count);

			if (m_buf != -1)
			{
				if (count < 1)
					return 0;

				buffer[offset] = (byte)m_buf;
				m_buf = -1;
				return 1;
			}

			return s.Read(buffer, offset, count);
		}

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override int Read(Span<byte> buffer)
        {
			if (m_buf != -1)
			{
                if (buffer.IsEmpty)
                    return 0;

                buffer[0] = (byte)m_buf;
                m_buf = -1;
                return 1;
            }

            return s.Read(buffer);
        }
#endif

        public override int ReadByte()
		{
			if (m_buf != -1)
			{
				int tmp = m_buf;
				m_buf = -1;
				return tmp;
			}

			return base.ReadByte();
		}

		public virtual void Unread(int b)
		{
			if (m_buf != -1)
				throw new InvalidOperationException("Can only push back one byte");

			m_buf = b & 0xFF;
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/PushbackStream.cs`.

**Classes defined**: PushbackStream



## Detailed Walkthrough

### Code Structure

- Total lines: 84
- Code lines: 64
- Comment lines: 4
- Blank lines: 16

### Main Components

**Classes** (1):
- `PushbackStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

