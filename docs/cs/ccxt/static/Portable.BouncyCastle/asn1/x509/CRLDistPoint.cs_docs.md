# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CRLDistPoint.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CRLDistPoint.cs`
- **Size**: 2,135 bytes
- **Lines**: 86
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Text;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
    public class CrlDistPoint
        : Asn1Encodable
    {
		public static CrlDistPoint GetInstance(Asn1TaggedObject obj, bool explicitly)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, explicitly));
        }

		public static CrlDistPoint GetInstance(object obj)
        {
            if (obj is CrlDistPoint)
                return (CrlDistPoint)obj;
            if (obj == null)
                return null;
            return new CrlDistPoint(Asn1Sequence.GetInstance(obj));
		}

        public static CrlDistPoint FromExtensions(X509Extensions extensions)
        {
            return GetInstance(X509Extensions.GetExtensionParsedValue(extensions, X509Extensions.CrlDistributionPoints));
        }

        internal readonly Asn1Sequence seq;

        private CrlDistPoint(
            Asn1Sequence seq)
        {
            this.seq = seq;
        }

		public CrlDistPoint(
            DistributionPoint[] points)
        {
			seq = new DerSequence(points);
        }

		/**
         * Return the distribution points making up the sequence.
         *
         * @return DistributionPoint[]
         */
        public DistributionPoint[] GetDistributionPoints()
        {
            DistributionPoint[] dp = new DistributionPoint[seq.Count];

			for (int i = 0; i != seq.Count; ++i)
            {
                dp[i] = DistributionPoint.GetInstance(seq[i]);
            }

			return dp;
        }

		/**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         * CrlDistPoint ::= Sequence SIZE {1..MAX} OF DistributionPoint
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
            return seq;
        }

		public override string ToString()
		{
			StringBuilder buf = new StringBuilder();
			buf.AppendLine("CRLDistPoint:");
            foreach (DistributionPoint dp in GetDistributionPoints())
			{
				buf.Append("    ")
				   .Append(dp)
                   .AppendLine();
			}
			return buf.ToString();
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CRLDistPoint.cs`.

**Classes defined**: CrlDistPoint

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 86
- Code lines: 73
- Comment lines: 11
- Blank lines: 2

### Main Components

**Classes** (1):
- `CrlDistPoint`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

