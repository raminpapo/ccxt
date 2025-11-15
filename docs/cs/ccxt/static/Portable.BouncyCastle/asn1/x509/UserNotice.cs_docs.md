# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/UserNotice.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/UserNotice.cs`
- **Size**: 3,126 bytes
- **Lines**: 110
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * <code>UserNotice</code> class, used in
     * <code>CertificatePolicies</code> X509 extensions (in policy
     * qualifiers).
     * <pre>
     * UserNotice ::= Sequence {
     *      noticeRef        NoticeReference OPTIONAL,
     *      explicitText     DisplayText OPTIONAL}
     *
     * </pre>
     *
     * @see PolicyQualifierId
     * @see PolicyInformation
     */
    public class UserNotice
        : Asn1Encodable
    {
        private readonly NoticeReference noticeRef;
        private readonly DisplayText explicitText;

        /**
         * Creates a new <code>UserNotice</code> instance.
         *
         * @param noticeRef a <code>NoticeReference</code> value
         * @param explicitText a <code>DisplayText</code> value
         */
        public UserNotice(
            NoticeReference	noticeRef,
            DisplayText		explicitText)
        {
            this.noticeRef = noticeRef;
            this.explicitText = explicitText;
        }

        /**
         * Creates a new <code>UserNotice</code> instance.
         *
         * @param noticeRef a <code>NoticeReference</code> value
         * @param str the explicitText field as a string.
         */
        public UserNotice(
            NoticeReference	noticeRef,
            string			str)
            : this(noticeRef, new DisplayText(str))
        {
        }

        private UserNotice(Asn1Sequence seq)
        {
            if (seq.Count == 2)
            {
                noticeRef = NoticeReference.GetInstance(seq[0]);
                explicitText = DisplayText.GetInstance(seq[1]);
            }
            else if (seq.Count == 1)
            {
                if (seq[0].ToAsn1Object() is Asn1Sequence)
                {
                    noticeRef = NoticeReference.GetInstance(seq[0]);
                    explicitText = null;
                }
                else
                {
                    noticeRef = null;
                    explicitText = DisplayText.GetInstance(seq[0]);
                }
            }
            else if (seq.Count == 0)
            {
                noticeRef = null;       // neither field set!
                explicitText = null;
            }
            else
            {
                throw new ArgumentException("Bad sequence size: " + seq.Count);
            }
        }

        public static UserNotice GetInstance(object obj)
        {
            if (obj is UserNotice)
                return (UserNotice)obj;
            if (obj == null)
                return null;
            return new UserNotice(Asn1Sequence.GetInstance(obj));
        }

        public virtual NoticeReference NoticeRef
        {
            get { return noticeRef; }
        }

        public virtual DisplayText ExplicitText
        {
            get { return explicitText; }
        }

        public override Asn1Object ToAsn1Object()
        {
            Asn1EncodableVector v = new Asn1EncodableVector();
            v.AddOptional(noticeRef, explicitText);
            return new DerSequence(v);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/UserNotice.cs`.

**Classes defined**: UserNotice

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 110
- Code lines: 101
- Comment lines: 26
- Blank lines: -17

### Main Components

**Classes** (1):
- `UserNotice`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

