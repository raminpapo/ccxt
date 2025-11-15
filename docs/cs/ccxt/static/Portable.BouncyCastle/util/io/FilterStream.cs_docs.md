# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/io/FilterStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/io/FilterStream.cs`
- **Size**: 1,946 bytes
- **Lines**: 82
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Utilities.IO
{
    public class FilterStream
        : Stream
    {
        protected readonly Stream s;

        public FilterStream(Stream s)
        {
            if (s == null)
                throw new ArgumentNullException(nameof(s));

            this.s = s;
        }
        public override bool CanRead
        {
            get { return s.CanRead; }
        }
        public override bool CanSeek
        {
            get { return s.CanSeek; }
        }
        public override bool CanWrite
        {
            get { return s.CanWrite; }
        }
        public override void Flush()
        {
            s.Flush();
        }
        public override long Length
        {
            get { return s.Length; }
        }
        public override long Position
        {
            get { return s.Position; }
            set { s.Position = value; }
        }
        public override int Read(byte[] buffer, int offset, int count)
        {
            return s.Read(buffer, offset, count);
        }
        public override int ReadByte()
        {
            return s.ReadByte();
        }
        public override long Seek(long offset, SeekOrigin origin)
        {
            return s.Seek(offset, origin);
        }
        public override void SetLength(long value)
        {
            s.SetLength(value);
        }
        public override void Write(byte[] buffer, int offset, int count)
        {
            s.Write(buffer, offset, count);
        }
        public override void WriteByte(byte value)
        {
            s.WriteByte(value);
        }
        protected void Detach(bool disposing)
        {
            base.Dispose(disposing);
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                s.Dispose();
            }

            base.Dispose(disposing);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/io/FilterStream.cs`.

**Classes defined**: FilterStream



## Detailed Walkthrough

### Code Structure

- Total lines: 82
- Code lines: 77
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `FilterStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

