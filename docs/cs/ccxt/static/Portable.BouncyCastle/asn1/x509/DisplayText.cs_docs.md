# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/DisplayText.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/DisplayText.cs`
- **Size**: 4,054 bytes
- **Lines**: 175
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
	/**
	 * <code>DisplayText</code> class, used in
	 * <code>CertificatePolicies</code> X509 V3 extensions (in policy qualifiers).
	 *
	 * <p>It stores a string in a chosen encoding.
	 * <pre>
	 * DisplayText ::= CHOICE {
	 *      ia5String        IA5String      (SIZE (1..200)),
	 *      visibleString    VisibleString  (SIZE (1..200)),
	 *      bmpString        BMPString      (SIZE (1..200)),
	 *      utf8String       UTF8String     (SIZE (1..200)) }
	 * </pre></p>
	 * @see PolicyQualifierInfo
	 * @see PolicyInformation
	 */
	public class DisplayText
		: Asn1Encodable, IAsn1Choice
	{
		/**
		 * Constant corresponding to ia5String encoding.
		 *
		 */
		public const int ContentTypeIA5String = 0;
		/**
		 * Constant corresponding to bmpString encoding.
		 *
		 */
		public const int ContentTypeBmpString = 1;
		/**
		 * Constant corresponding to utf8String encoding.
		 *
		 */
		public const int ContentTypeUtf8String = 2;
		/**
		 * Constant corresponding to visibleString encoding.
		 *
		 */
		public const int ContentTypeVisibleString = 3;
		/**
		 * Describe constant <code>DisplayTextMaximumSize</code> here.
		 *
		 */
		public const int DisplayTextMaximumSize = 200;

		internal readonly int contentType;
		internal readonly IAsn1String contents;

		/**
		 * Creates a new <code>DisplayText</code> instance.
		 *
		 * @param type the desired encoding type for the text.
		 * @param text the text to store. Strings longer than 200
		 * characters are truncated.
		 */
		public DisplayText(
			int		type,
			string	text)
		{
			if (text.Length > DisplayTextMaximumSize)
			{
				// RFC3280 limits these strings to 200 chars
				// truncate the string
				text = text.Substring(0, DisplayTextMaximumSize);
			}

			contentType = type;
			switch (type)
			{
				case ContentTypeIA5String:
					contents = (IAsn1String)new DerIA5String (text);
					break;
				case ContentTypeUtf8String:
					contents = (IAsn1String)new DerUtf8String(text);
					break;
				case ContentTypeVisibleString:
					contents = (IAsn1String)new DerVisibleString(text);
					break;
				case ContentTypeBmpString:
					contents = (IAsn1String)new DerBmpString(text);
					break;
				default:
					contents = (IAsn1String)new DerUtf8String(text);
					break;
			}
		}

//		/**
//		 * return true if the passed in string can be represented without
//		 * loss as a PrintableString, false otherwise.
//		 */
//		private bool CanBePrintable(
//			string str)
//		{
//			for (int i = str.Length - 1; i >= 0; i--)
//			{
//				if (str[i] > 0x007f)
//				{
//					return false;
//				}
//			}
//
//			return true;
//		}

		/**
		 * Creates a new <code>DisplayText</code> instance.
		 *
		 * @param text the text to encapsulate. Strings longer than 200
		 * characters are truncated.
		 */
		public DisplayText(
			string text)
		{
			// by default use UTF8String
			if (text.Length > DisplayTextMaximumSize)
			{
				text = text.Substring(0, DisplayTextMaximumSize);
			}

			contentType = ContentTypeUtf8String;
			contents = new DerUtf8String(text);
		}

		/**
		 * Creates a new <code>DisplayText</code> instance.
		 * <p>Useful when reading back a <code>DisplayText</code> class
		 * from it's Asn1Encodable form.</p>
		 *
		 * @param contents an <code>Asn1Encodable</code> instance.
		 */
		public DisplayText(
			IAsn1String contents)
		{
			this.contents = contents;
		}

		public static DisplayText GetInstance(
			object obj)
		{
			if (obj is IAsn1String)
			{
				return new DisplayText((IAsn1String) obj);
			}

			if (obj is DisplayText)
			{
				return (DisplayText) obj;
			}

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		public override Asn1Object ToAsn1Object()
		{
			return (Asn1Object) contents;
		}

		/**
		 * Returns the stored <code>string</code> object.
		 *
		 * @return the stored text as a <code>string</code>.
		 */
		public string GetString()
		{
			return contents.GetString();
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/DisplayText.cs`.

**Classes defined**: DisplayText

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 175
- Code lines: 140
- Comment lines: 80
- Blank lines: -45

### Main Components

**Classes** (1):
- `DisplayText`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

