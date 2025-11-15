# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/DigestInfo.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/DigestInfo.cs`
- **Size**: 1,799 bytes
- **Lines**: 78
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * The DigestInfo object.
     * <pre>
     * DigestInfo::=Sequence{
     *          digestAlgorithm  AlgorithmIdentifier,
     *          digest OCTET STRING }
     * </pre>
     */
    public class DigestInfo
        : Asn1Encodable
    {
        private readonly byte[] digest;
        private readonly AlgorithmIdentifier algID;

		public static DigestInfo GetInstance(
            Asn1TaggedObject	obj,
            bool				explicitly)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, explicitly));
        }

		public static DigestInfo GetInstance(
            object obj)
        {
            if (obj is DigestInfo)
            {
                return (DigestInfo) obj;
            }

			if (obj is Asn1Sequence)
            {
                return new DigestInfo((Asn1Sequence) obj);
            }

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		public DigestInfo(
            AlgorithmIdentifier	algID,
            byte[]				digest)
        {
            this.digest = digest;
            this.algID = algID;
        }

		private DigestInfo(
            Asn1Sequence seq)
        {
			if (seq.Count != 2)
				throw new ArgumentException("Wrong number of elements in sequence", "seq");

            algID = AlgorithmIdentifier.GetInstance(seq[0]);
			digest = Asn1OctetString.GetInstance(seq[1]).GetOctets();
		}

		public AlgorithmIdentifier AlgorithmID
		{
			get { return algID; }
		}

		public byte[] GetDigest()
        {
            return digest;
        }

		public override Asn1Object ToAsn1Object()
        {
			return new DerSequence(algID, new DerOctetString(digest));
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/DigestInfo.cs`.

**Classes defined**: DigestInfo

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 78
- Code lines: 65
- Comment lines: 8
- Blank lines: 5

### Main Components

**Classes** (1):
- `DigestInfo`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

