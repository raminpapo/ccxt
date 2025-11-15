# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyMappings.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyMappings.cs`
- **Size**: 1,379 bytes
- **Lines**: 63
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Collections.Generic;

namespace Org.BouncyCastle.Asn1.X509
{
	/**
	 * PolicyMappings V3 extension, described in RFC3280.
	 * <pre>
	 *    PolicyMappings ::= Sequence SIZE (1..MAX) OF Sequence {
	 *      issuerDomainPolicy      CertPolicyId,
	 *      subjectDomainPolicy     CertPolicyId }
	 * </pre>
	 *
	 * @see <a href="http://www.faqs.org/rfc/rfc3280.txt">RFC 3280, section 4.2.1.6</a>
	 */
	public class PolicyMappings
		: Asn1Encodable
	{
		private readonly Asn1Sequence seq;

		/**
		 * Creates a new <code>PolicyMappings</code> instance.
		 *
		 * @param seq an <code>Asn1Sequence</code> constructed as specified
		 * in RFC 3280
		 */
		public PolicyMappings(
			Asn1Sequence seq)
		{
			this.seq = seq;
		}

        /**
		 * Creates a new <code>PolicyMappings</code> instance.
		 *
		 * @param mappings a <code>HashMap</code> value that maps
		 * <code>string</code> oids
		 * to other <code>string</code> oids.
		 */
		public PolicyMappings(IDictionary<string, string> mappings)
		{
			Asn1EncodableVector v = new Asn1EncodableVector();

			foreach (var entry in mappings)
			{
				string idp = entry.Key;
				string sdp = entry.Value;

				v.Add(
					new DerSequence(
						new DerObjectIdentifier(idp),
						new DerObjectIdentifier(sdp)));
			}

			seq = new DerSequence(v);
		}

		public override Asn1Object ToAsn1Object()
		{
			return seq;
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyMappings.cs`.

**Classes defined**: PolicyMappings

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 55
- Comment lines: 23
- Blank lines: -15

### Main Components

**Classes** (1):
- `PolicyMappings`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `http://www.faqs.org/rfc/rfc3280.txt` (referenced)



## Testing & Execution

**To execute this C# file:**

