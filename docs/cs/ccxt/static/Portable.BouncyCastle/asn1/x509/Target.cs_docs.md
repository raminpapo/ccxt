# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Target.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Target.cs`
- **Size**: 3,160 bytes
- **Lines**: 142
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
	/**
	 * Target structure used in target information extension for attribute
	 * certificates from RFC 3281.
	 * 
	 * <pre>
	 *     Target  ::= CHOICE {
	 *       targetName          [0] GeneralName,
	 *       targetGroup         [1] GeneralName,
	 *       targetCert          [2] TargetCert
	 *     }
	 * </pre>
	 * 
	 * <p>
	 * The targetCert field is currently not supported and must not be used
	 * according to RFC 3281.</p>
	 */
	public class Target
		: Asn1Encodable, IAsn1Choice
	{
		public enum Choice
		{
			Name = 0,
			Group = 1
		};

		private readonly GeneralName targetName;
		private readonly GeneralName targetGroup;

		/**
		* Creates an instance of a Target from the given object.
		* <p>
		* <code>obj</code> can be a Target or a {@link Asn1TaggedObject}</p>
		* 
		* @param obj The object.
		* @return A Target instance.
		* @throws ArgumentException if the given object cannot be
		*             interpreted as Target.
		*/
		public static Target GetInstance(
			object obj)
		{
			if (obj is Target)
			{
				return (Target) obj;
			}

			if (obj is Asn1TaggedObject)
			{
				return new Target((Asn1TaggedObject) obj);
			}

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		/**
		 * Constructor from Asn1TaggedObject.
		 * 
		 * @param tagObj The tagged object.
		 * @throws ArgumentException if the encoding is wrong.
		 */
		private Target(
			Asn1TaggedObject tagObj)
		{
			switch ((Choice) tagObj.TagNo)
			{
				case Choice.Name:	// GeneralName is already a choice so explicit
					targetName = GeneralName.GetInstance(tagObj, true);
					break;
				case Choice.Group:
					targetGroup = GeneralName.GetInstance(tagObj, true);
					break;
				default:
					throw new ArgumentException("unknown tag: " + tagObj.TagNo);
			}
		}

		/**
		 * Constructor from given details.
		 * <p>
		 * Exactly one of the parameters must be not <code>null</code>.</p>
		 *
		 * @param type the choice type to apply to the name.
		 * @param name the general name.
		 * @throws ArgumentException if type is invalid.
		 */
		public Target(
			Choice		type,
			GeneralName	name)
			: this(new DerTaggedObject((int) type, name))
		{
		}

		/**
		 * @return Returns the targetGroup.
		 */
		public virtual GeneralName TargetGroup
		{
			get { return targetGroup; }
		}

		/**
		 * @return Returns the targetName.
		 */
		public virtual GeneralName TargetName
		{
			get { return targetName; }
		}

		/**
		 * Produce an object suitable for an Asn1OutputStream.
		 * 
		 * Returns:
		 * 
		 * <pre>
		 *     Target  ::= CHOICE {
		 *       targetName          [0] GeneralName,
		 *       targetGroup         [1] GeneralName,
		 *       targetCert          [2] TargetCert
		 *     }
		 * </pre>
		 * 
		 * @return an Asn1Object
		 */
		public override Asn1Object ToAsn1Object()
		{
			// GeneralName is a choice already so most be explicitly tagged
			if (targetName != null)
			{
				return new DerTaggedObject(true, 0, targetName);
			}

			return new DerTaggedObject(true, 1, targetGroup);
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/Target.cs`.

**Classes defined**: Target

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 142
- Code lines: 128
- Comment lines: 63
- Blank lines: -49

### Main Components

**Classes** (1):
- `Target`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

