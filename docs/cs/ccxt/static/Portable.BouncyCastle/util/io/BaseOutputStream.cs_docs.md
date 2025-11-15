# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/BaseOutputStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/BaseOutputStream.cs`
- **Size**: 1,570 bytes
- **Lines**: 43
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Utilities.IO
{
    public abstract class BaseOutputStream
        : Stream
    {
        public sealed override bool CanRead { get { return false; } }
        public sealed override bool CanSeek { get { return false; } }
        public sealed override bool CanWrite { get { return true; } }

#if NETCOREAPP2_0_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public override void CopyTo(Stream destination, int bufferSize) { throw new NotSupportedException(); }
#endif
        public override void Flush() {}
        public sealed override long Length { get { throw new NotSupportedException(); } }
        public sealed override long Position
        {
            get { throw new NotSupportedException(); }
            set { throw new NotSupportedException(); }
        }
        public sealed override int Read(byte[] buffer, int offset, int count) { throw new NotSupportedException(); }
        public sealed override long Seek(long offset, SeekOrigin origin) { throw new NotSupportedException(); }
        public sealed override void SetLength(long value) { throw new NotSupportedException(); }

        public override void Write(byte[] buffer, int offset, int count)
        {
            Streams.ValidateBufferArguments(buffer, offset, count);

            for (int i = 0; i < count; ++i)
            {
                WriteByte(buffer[offset + i]);
            }
        }

        public virtual void Write(params byte[] buffer)
        {
            Write(buffer, 0, buffer.Length);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/BaseOutputStream.cs`.

**Classes defined**: BaseOutputStream



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 35
- Comment lines: 2
- Blank lines: 6

### Main Components

**Classes** (1):
- `BaseOutputStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

