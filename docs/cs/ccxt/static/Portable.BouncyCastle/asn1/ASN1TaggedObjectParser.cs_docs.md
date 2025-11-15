# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/ASN1TaggedObjectParser.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/ASN1TaggedObjectParser.cs`
- **Size**: 1,177 bytes
- **Lines**: 36
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Asn1
{
	public interface Asn1TaggedObjectParser
		: IAsn1Convertible
	{
        int TagClass { get; }

		int TagNo { get; }

        bool HasContextTag(int tagNo);

        bool HasTag(int tagClass, int tagNo);

        /// <exception cref="IOException"/>
        IAsn1Convertible ParseBaseUniversal(bool declaredExplicit, int baseTagNo);

        /// <summary>Needed for open types, until we have better type-guided parsing support.</summary>
        /// <remarks>
        /// Use sparingly for other purposes, and prefer <see cref="ParseExplicitBaseTagged"/> or
        /// <see cref="ParseBaseUniversal(bool, int)"/> where possible. Before using, check for matching tag
        /// <see cref="TagClass">class</see> and <see cref="TagNo">number</see>.
        /// </remarks>
        /// <exception cref="IOException"/>
        IAsn1Convertible ParseExplicitBaseObject();

        /// <exception cref="IOException"/>
        Asn1TaggedObjectParser ParseExplicitBaseTagged();

        /// <exception cref="IOException"/>
        Asn1TaggedObjectParser ParseImplicitBaseTagged(int baseTagClass, int baseTagNo);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/ASN1TaggedObjectParser.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 17
- Comment lines: 10
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

