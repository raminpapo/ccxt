# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/BerBitStringParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/BerBitStringParser.cs`
- **Size**: 1,479 bytes
- **Lines**: 57
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.IO;

using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Asn1
{
    /// <summary>A parser for indefinite-length BIT STRINGs.</summary>
    internal class BerBitStringParser
        : Asn1BitStringParser
    {
        private readonly Asn1StreamParser m_parser;

        private ConstructedBitStream m_bitStream;

        internal BerBitStringParser(Asn1StreamParser parser)
        {
            m_parser = parser;
        }

        public Stream GetOctetStream()
        {
            return m_bitStream = new ConstructedBitStream(m_parser, true);
        }

        public Stream GetBitStream()
        {
            return m_bitStream = new ConstructedBitStream(m_parser, false);
        }

        public int PadBits
        {
            get { return m_bitStream.PadBits; }
        }

        public Asn1Object ToAsn1Object()
        {
            try
            {
                return Parse(m_parser);
            }
            catch (IOException e)
            {
                throw new Asn1ParsingException("IOException converting stream to byte array: " + e.Message, e);
            }
        }

        internal static BerBitString Parse(Asn1StreamParser sp)
        {
            ConstructedBitStream bitStream = new ConstructedBitStream(sp, false);
            byte[] data = Streams.ReadAll(bitStream);
            int padBits = bitStream.PadBits;
            return new BerBitString(data, padBits);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/BerBitStringParser.cs`.

**Classes defined**: BerBitStringParser



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 46
- Comment lines: 1
- Blank lines: 10

### Main Components

**Classes** (1):
- `BerBitStringParser`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

