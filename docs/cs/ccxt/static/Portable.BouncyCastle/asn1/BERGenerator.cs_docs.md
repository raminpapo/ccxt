# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/BERGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/BERGenerator.cs`
- **Size**: 2,355 bytes
- **Lines**: 107
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.IO;

using Org.BouncyCastle.Utilities.IO;

namespace Org.BouncyCastle.Asn1
{
    public abstract class BerGenerator
        : Asn1Generator
    {
        private bool      _tagged = false;
        private bool      _isExplicit;
        private int          _tagNo;

        protected BerGenerator(
            Stream outStream)
            : base(outStream)
        {
        }

        protected BerGenerator(
            Stream outStream,
            int tagNo,
            bool isExplicit)
            : base(outStream)
        {
            _tagged = true;
            _isExplicit = isExplicit;
            _tagNo = tagNo;
        }

		public override void AddObject(Asn1Encodable obj)
		{
            obj.EncodeTo(Out);
		}

        public override void AddObject(Asn1Object obj)
        {
            obj.EncodeTo(Out);
        }

        public override Stream GetRawOutputStream()
        {
            return Out;
        }

		public override void Close()
		{
			WriteBerEnd();
		}

        private void WriteHdr(
            int tag)
        {
            Out.WriteByte((byte) tag);
            Out.WriteByte(0x80);
        }

        protected void WriteBerHeader(
            int tag)
        {
            if (_tagged)
            {
                int tagNum = _tagNo | Asn1Tags.ContextSpecific;

                if (_isExplicit)
                {
                    WriteHdr(tagNum | Asn1Tags.Constructed);
                    WriteHdr(tag);
                }
                else
                {
                    if ((tag & Asn1Tags.Constructed) != 0)
                    {
                        WriteHdr(tagNum | Asn1Tags.Constructed);
                    }
                    else
                    {
                        WriteHdr(tagNum);
                    }
                }
            }
            else
            {
                WriteHdr(tag);
            }
        }

		protected void WriteBerBody(
            Stream contentStream)
        {
			Streams.PipeAll(contentStream, Out);
        }

		protected void WriteBerEnd()
        {
            Out.WriteByte(0x00);
            Out.WriteByte(0x00);

            if (_tagged && _isExplicit)  // write extra end for tag header
            {
                Out.WriteByte(0x00);
                Out.WriteByte(0x00);
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/BERGenerator.cs`.

**Classes defined**: BerGenerator



## Detailed Walkthrough

### Code Structure

- Total lines: 107
- Code lines: 92
- Comment lines: 0
- Blank lines: 15

### Main Components

**Classes** (1):
- `BerGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

