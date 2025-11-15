# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509Extension.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509Extension.cs`
- **Size**: 1,900 bytes
- **Lines**: 80
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * an object for the elements in the X.509 V3 extension block.
     */
    public class X509Extension
    {
        internal bool				critical;
        internal Asn1OctetString	value;

		public X509Extension(
            DerBoolean		critical,
            Asn1OctetString	value)
        {
            if (critical == null)
            {
                throw new ArgumentNullException("critical");
            }

			this.critical = critical.IsTrue;
            this.value = value;
        }

		public X509Extension(
            bool			critical,
            Asn1OctetString	value)
        {
            this.critical = critical;
            this.value = value;
        }

		public bool IsCritical { get { return critical; } }

		public Asn1OctetString Value { get { return value; } }

		public Asn1Encodable GetParsedValue()
		{
			return ConvertValueToObject(this);
		}

		public override int GetHashCode()
        {
			int vh = this.Value.GetHashCode();

			return IsCritical ? vh : ~vh;
        }

		public override bool Equals(
            object obj)
        {
            X509Extension other = obj as X509Extension;
            if (other == null)
            {
                return false;
            }

			return Value.Equals(other.Value) && IsCritical == other.IsCritical;
        }

		/// <sumary>Convert the value of the passed in extension to an object.</sumary>
		/// <param name="ext">The extension to parse.</param>
		/// <returns>The object the value string contains.</returns>
		/// <exception cref="ArgumentException">If conversion is not possible.</exception>
		public static Asn1Object ConvertValueToObject(
			X509Extension ext)
		{
			try
			{
				return Asn1Object.FromByteArray(ext.Value.GetOctets());
			}
			catch (Exception e)
			{
				throw new ArgumentException("can't convert extension", e);
			}
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509Extension.cs`.

**Classes defined**: X509Extension

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 63
- Comment lines: 7
- Blank lines: 10

### Main Components

**Classes** (1):
- `X509Extension`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

