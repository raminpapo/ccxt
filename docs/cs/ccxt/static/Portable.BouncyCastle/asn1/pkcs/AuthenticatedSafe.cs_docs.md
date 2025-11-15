# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/AuthenticatedSafe.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/AuthenticatedSafe.cs`
- **Size**: 1,508 bytes
- **Lines**: 64
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Asn1;

namespace Org.BouncyCastle.Asn1.Pkcs
{
    public class AuthenticatedSafe
        : Asn1Encodable
    {
        private static ContentInfo[] Copy(ContentInfo[] info)
        {
            return (ContentInfo[])info.Clone();
        }

        public static AuthenticatedSafe GetInstance(object obj)
        {
            if (obj is AuthenticatedSafe)
                return (AuthenticatedSafe)obj;
            if (obj == null)
                return null;
            return new AuthenticatedSafe(Asn1Sequence.GetInstance(obj));
        }

        private readonly ContentInfo[] info;
        private readonly bool isBer;

		private AuthenticatedSafe(Asn1Sequence seq)
        {
            info = new ContentInfo[seq.Count];

            for (int i = 0; i != info.Length; i++)
            {
                info[i] = ContentInfo.GetInstance(seq[i]);
            }

            isBer = seq is BerSequence;
        }

		public AuthenticatedSafe(
            ContentInfo[] info)
        {
            this.info = Copy(info);
            this.isBer = true;
        }

		public ContentInfo[] GetContentInfo()
        {
            return Copy(info);
        }

        public override Asn1Object ToAsn1Object()
        {
            if (isBer)
            {
                return new BerSequence(info);
            }

            // TODO bc-java uses DL sequence
            //return new DLSequence(info);
            return new DerSequence(info);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/AuthenticatedSafe.cs`.

**Classes defined**: AuthenticatedSafe



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 50
- Comment lines: 2
- Blank lines: 12

### Main Components

**Classes** (1):
- `AuthenticatedSafe`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

