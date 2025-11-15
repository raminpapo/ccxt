# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AttCertValidityPeriod.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AttCertValidityPeriod.cs`
- **Size**: 2,063 bytes
- **Lines**: 79
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
    public class AttCertValidityPeriod
        : Asn1Encodable
    {
        private readonly DerGeneralizedTime	notBeforeTime;
        private readonly DerGeneralizedTime	notAfterTime;

		public static AttCertValidityPeriod GetInstance(
            object obj)
        {
            if (obj is AttCertValidityPeriod || obj == null)
            {
                return (AttCertValidityPeriod) obj;
            }

			if (obj is Asn1Sequence)
            {
                return new AttCertValidityPeriod((Asn1Sequence) obj);
            }

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		public static AttCertValidityPeriod GetInstance(
            Asn1TaggedObject	obj,
            bool				explicitly)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, explicitly));
        }

		private AttCertValidityPeriod(
            Asn1Sequence seq)
        {
			if (seq.Count != 2)
				throw new ArgumentException("Bad sequence size: " + seq.Count);

			notBeforeTime = DerGeneralizedTime.GetInstance(seq[0]);
			notAfterTime = DerGeneralizedTime.GetInstance(seq[1]);
        }

		public AttCertValidityPeriod(
            DerGeneralizedTime	notBeforeTime,
            DerGeneralizedTime	notAfterTime)
        {
            this.notBeforeTime = notBeforeTime;
            this.notAfterTime = notAfterTime;
        }

		public DerGeneralizedTime NotBeforeTime
		{
			get { return notBeforeTime; }
		}

		public DerGeneralizedTime NotAfterTime
		{
			get { return notAfterTime; }
		}

		/**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         *  AttCertValidityPeriod  ::= Sequence {
         *       notBeforeTime  GeneralizedTime,
         *       notAfterTime   GeneralizedTime
         *  }
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
			return new DerSequence(notBeforeTime, notAfterTime);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AttCertValidityPeriod.cs`.

**Classes defined**: AttCertValidityPeriod

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 79
- Code lines: 66
- Comment lines: 9
- Blank lines: 4

### Main Components

**Classes** (1):
- `AttCertValidityPeriod`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

