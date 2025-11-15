# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Targets.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Targets.cs`
- **Size**: 2,832 bytes
- **Lines**: 124
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
	/**
	 * Targets structure used in target information extension for attribute
	 * certificates from RFC 3281.
	 * 
	 * <pre>
	 *            Targets ::= SEQUENCE OF Target
	 *           
	 *            Target  ::= CHOICE {
	 *              targetName          [0] GeneralName,
	 *              targetGroup         [1] GeneralName,
	 *              targetCert          [2] TargetCert
	 *            }
	 *           
	 *            TargetCert  ::= SEQUENCE {
	 *              targetCertificate    IssuerSerial,
	 *              targetName           GeneralName OPTIONAL,
	 *              certDigestInfo       ObjectDigestInfo OPTIONAL
	 *            }
	 * </pre>
	 * 
	 * @see org.bouncycastle.asn1.x509.Target
	 * @see org.bouncycastle.asn1.x509.TargetInformation
	 */
	public class Targets
		: Asn1Encodable
	{
		private readonly Asn1Sequence targets;

		/**
		 * Creates an instance of a Targets from the given object.
		 * <p>
		 * <code>obj</code> can be a Targets or a {@link Asn1Sequence}</p>
		 * 
		 * @param obj The object.
		 * @return A Targets instance.
		 * @throws ArgumentException if the given object cannot be interpreted as Target.
		 */
		public static Targets GetInstance(
			object obj)
		{
			if (obj is Targets)
			{
				return (Targets) obj;
			}

			if (obj is Asn1Sequence)
			{
				return new Targets((Asn1Sequence) obj);
			}

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		/**
		 * Constructor from Asn1Sequence.
		 * 
		 * @param targets The ASN.1 SEQUENCE.
		 * @throws ArgumentException if the contents of the sequence are
		 *             invalid.
		 */
		private Targets(
			Asn1Sequence targets)
		{
			this.targets = targets;
		}

		/**
		 * Constructor from given targets.
		 * <p>
		 * The ArrayList is copied.</p>
		 * 
		 * @param targets An <code>ArrayList</code> of {@link Target}s.
		 * @see Target
		 * @throws ArgumentException if the ArrayList contains not only Targets.
		 */
		public Targets(
			Target[] targets)
		{
			this.targets = new DerSequence(targets);
		}

		/**
		 * Returns the targets in an <code>ArrayList</code>.
		 * <p>
		 * The ArrayList is cloned before it is returned.</p>
		 * 
		 * @return Returns the targets.
		 */
		public virtual Target[] GetTargets()
		{
			Target[] result = new Target[targets.Count];

			for (int i = 0; i < targets.Count; ++i)
			{
				result[i] = Target.GetInstance(targets[i]);
			}

			return result;
		}

		/**
		 * Produce an object suitable for an Asn1OutputStream.
		 * 
		 * Returns:
		 * 
		 * <pre>
		 *            Targets ::= SEQUENCE OF Target
		 * </pre>
		 * 
		 * @return an Asn1Object
		 */
		public override Asn1Object ToAsn1Object()
		{
			return targets;
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Targets.cs`.

**Classes defined**: Targets

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 124
- Code lines: 112
- Comment lines: 66
- Blank lines: -54

### Main Components

**Classes** (1):
- `Targets`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

