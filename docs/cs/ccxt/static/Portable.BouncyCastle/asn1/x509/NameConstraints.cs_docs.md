# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/NameConstraints.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/NameConstraints.cs`
- **Size**: 2,265 bytes
- **Lines**: 102
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Collections.Generic;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
	public class NameConstraints
		: Asn1Encodable
	{
		private Asn1Sequence permitted, excluded;

		public static NameConstraints GetInstance(
			object obj)
		{
			if (obj == null || obj is NameConstraints)
			{
				return (NameConstraints) obj;
			}

			if (obj is Asn1Sequence)
			{
				return new NameConstraints((Asn1Sequence) obj);
			}

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		public NameConstraints(
			Asn1Sequence seq)
		{
			foreach (Asn1TaggedObject o in seq)
			{
				switch (o.TagNo)
				{
					case 0:
						permitted = Asn1Sequence.GetInstance(o, false);
						break;
					case 1:
						excluded = Asn1Sequence.GetInstance(o, false);
						break;
				}
			}
		}

        /**
		 * Constructor from a given details.
		 *
		 * <p>permitted and excluded are Vectors of GeneralSubtree objects.</p>
		 *
		 * @param permitted Permitted subtrees
		 * @param excluded Excluded subtrees
		 */
		public NameConstraints(
			IList<GeneralSubtree> permitted,
			IList<GeneralSubtree> excluded)
		{
			if (permitted != null)
			{
				this.permitted = CreateSequence(permitted);
			}

			if (excluded != null)
			{
				this.excluded = CreateSequence(excluded);
			}
		}

		private DerSequence CreateSequence(IList<GeneralSubtree> subtrees)
		{
            GeneralSubtree[] gsts = new GeneralSubtree[subtrees.Count];
            for (int i = 0; i < subtrees.Count; ++i)
            {
                gsts[i] = subtrees[i];
            }
            return new DerSequence(gsts);
		}

		public Asn1Sequence PermittedSubtrees
		{
			get { return permitted; }
		}

		public Asn1Sequence ExcludedSubtrees
		{
			get { return excluded; }
		}

		/*
		 * NameConstraints ::= SEQUENCE { permittedSubtrees [0] GeneralSubtrees
		 * OPTIONAL, excludedSubtrees [1] GeneralSubtrees OPTIONAL }
		 */
        public override Asn1Object ToAsn1Object()
        {
            Asn1EncodableVector v = new Asn1EncodableVector();
            v.AddOptionalTagged(false, 0, permitted);
            v.AddOptionalTagged(false, 1, excluded);
            return new DerSequence(v);
        }
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/NameConstraints.cs`.

**Classes defined**: NameConstraints

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 102
- Code lines: 89
- Comment lines: 12
- Blank lines: 1

### Main Components

**Classes** (1):
- `NameConstraints`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

