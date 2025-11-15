# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/ContentInfo.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/ContentInfo.cs`
- **Size**: 1,837 bytes
- **Lines**: 72
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.Pkcs
{
    public class ContentInfo
        : Asn1Encodable
    {
        private readonly DerObjectIdentifier	contentType;
        private readonly Asn1Encodable			content;

        public static ContentInfo GetInstance(object obj)
        {
            if (obj == null)
                return null;
            ContentInfo existing = obj as ContentInfo;
            if (existing != null)
                return existing;
            return new ContentInfo(Asn1Sequence.GetInstance(obj));
        }

        private ContentInfo(
            Asn1Sequence seq)
        {
            contentType = (DerObjectIdentifier) seq[0];

            if (seq.Count > 1)
            {
                content = ((Asn1TaggedObject) seq[1]).GetObject();
            }
        }

        public ContentInfo(
            DerObjectIdentifier	contentType,
            Asn1Encodable		content)
        {
            this.contentType = contentType;
            this.content = content;
        }

        public DerObjectIdentifier ContentType
        {
            get { return contentType; }
        }

        public Asn1Encodable Content
        {
            get { return content; }
        }

        /**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         * ContentInfo ::= Sequence {
         *          contentType ContentType,
         *          content
         *          [0] EXPLICIT ANY DEFINED BY contentType OPTIONAL }
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
            Asn1EncodableVector v = new Asn1EncodableVector(contentType);

            if (content != null)
            {
                v.Add(new BerTaggedObject(0, content));
            }

            return new BerSequence(v);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/ContentInfo.cs`.

**Classes defined**: ContentInfo

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 61
- Comment lines: 9
- Blank lines: 2

### Main Components

**Classes** (1):
- `ContentInfo`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

