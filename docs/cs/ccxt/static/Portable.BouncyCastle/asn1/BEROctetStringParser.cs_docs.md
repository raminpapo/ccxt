# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/BEROctetStringParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/BEROctetStringParser.cs`
- **Size**: 963 bytes
- **Lines**: 41
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Asn1
{
    public class BerOctetStringParser
        : Asn1OctetStringParser
    {
        private readonly Asn1StreamParser _parser;

        internal BerOctetStringParser(Asn1StreamParser parser)
        {
            _parser = parser;
        }

        public Stream GetOctetStream()
        {
            return new ConstructedOctetStream(_parser);
        }

        public Asn1Object ToAsn1Object()
        {
            try
            {
                return Parse(_parser);
            }
            catch (IOException e)
            {
                throw new Asn1ParsingException("IOException converting stream to byte array: " + e.Message, e);
            }
        }

        internal static BerOctetString Parse(Asn1StreamParser sp)
        {
            return new BerOctetString(Streams.ReadAll(new ConstructedOctetStream(sp)));
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/BEROctetStringParser.cs`.

**Classes defined**: BerOctetStringParser



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 34
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `BerOctetStringParser`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

