# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AccessDescription.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AccessDescription.cs`
- **Size**: 1,968 bytes
- **Lines**: 86
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
	/**
	 * The AccessDescription object.
	 * <pre>
	 * AccessDescription  ::=  SEQUENCE {
	 *       accessMethod          OBJECT IDENTIFIER,
	 *       accessLocation        GeneralName  }
	 * </pre>
	 */
	public class AccessDescription
		: Asn1Encodable
	{
		public readonly static DerObjectIdentifier IdADCAIssuers = new DerObjectIdentifier("1.3.6.1.5.5.7.48.2");
		public readonly static DerObjectIdentifier IdADOcsp = new DerObjectIdentifier("1.3.6.1.5.5.7.48.1");

		private readonly DerObjectIdentifier accessMethod;
		private readonly GeneralName accessLocation;

		public static AccessDescription GetInstance(
			object obj)
		{
			if (obj is AccessDescription)
				return (AccessDescription) obj;

			if (obj is Asn1Sequence)
				return new AccessDescription((Asn1Sequence) obj);

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		private AccessDescription(
			Asn1Sequence seq)
		{
			if (seq.Count != 2)
				throw new ArgumentException("wrong number of elements in sequence");

			accessMethod = DerObjectIdentifier.GetInstance(seq[0]);
			accessLocation = GeneralName.GetInstance(seq[1]);
		}

		/**
		 * create an AccessDescription with the oid and location provided.
		 */
		public AccessDescription(
			DerObjectIdentifier	oid,
			GeneralName			location)
		{
			accessMethod = oid;
			accessLocation = location;
		}

		/**
		 *
		 * @return the access method.
		 */
		public DerObjectIdentifier AccessMethod
		{
			get { return accessMethod; }
		}

		/**
		 *
		 * @return the access location
		 */
		public GeneralName AccessLocation
		{
			get { return accessLocation; }
		}

		public override Asn1Object ToAsn1Object()
		{
			return new DerSequence(accessMethod, accessLocation);
		}

		public override string ToString()
		{
			return "AccessDescription: Oid(" + this.accessMethod.Id + ")";
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AccessDescription.cs`.

**Classes defined**: AccessDescription

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 86
- Code lines: 72
- Comment lines: 19
- Blank lines: -5

### Main Components

**Classes** (1):
- `AccessDescription`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

