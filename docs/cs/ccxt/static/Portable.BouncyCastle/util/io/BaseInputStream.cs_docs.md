# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/BaseInputStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/BaseInputStream.cs`
- **Size**: 1,599 bytes
- **Lines**: 50
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Utilities.IO
{
    public abstract class BaseInputStream
        : Stream
    {
        public sealed override bool CanRead { get { return true; } }
        public sealed override bool CanSeek { get { return false; } }
        public sealed override bool CanWrite { get { return false; } }

        public sealed override void Flush() {}
        public sealed override long Length { get { throw new NotSupportedException(); } }
        public sealed override long Position
        {
            get { throw new NotSupportedException(); }
            set { throw new NotSupportedException(); }
        }

        public override int Read(byte[] buffer, int offset, int count)
        {
            Streams.ValidateBufferArguments(buffer, offset, count);

            int pos = 0;
            try
            {
                while (pos < count)
                {
                    int b = ReadByte();
                    if (b < 0)
                        break;

                    buffer[offset + pos++] = (byte)b;
                }
            }
            catch (IOException)
            {
                if (pos == 0)
                    throw;
            }
            return pos;
        }

        public sealed override long Seek(long offset, SeekOrigin origin) { throw new NotSupportedException(); }
        public sealed override void SetLength(long value) { throw new NotSupportedException(); }
        public sealed override void Write(byte[] buffer, int offset, int count) { throw new NotSupportedException(); }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/BaseInputStream.cs`.

**Classes defined**: BaseInputStream



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 43
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `BaseInputStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

