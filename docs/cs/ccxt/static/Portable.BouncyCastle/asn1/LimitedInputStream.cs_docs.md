# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/LimitedInputStream.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/LimitedInputStream.cs`
- **Size**: 700 bytes
- **Lines**: 33
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.IO;

using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Asn1
{
    internal abstract class LimitedInputStream
        : BaseInputStream
    {
        protected readonly Stream _in;
        private int _limit;

        internal LimitedInputStream(Stream inStream, int limit)
        {
            this._in = inStream;
            this._limit = limit;
        }

        internal virtual int Limit
        {
            get { return _limit; }
        }

        protected void SetParentEofDetect()
        {
            if (_in is IndefiniteLengthInputStream)
            {
                ((IndefiniteLengthInputStream)_in).SetEofOn00(true);
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/LimitedInputStream.cs`.

**Classes defined**: LimitedInputStream



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 27
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `LimitedInputStream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

