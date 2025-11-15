# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/encoders/UrlBase64Encoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/encoders/UrlBase64Encoder.cs`
- **Size**: 1,055 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;

namespace Org.BouncyCastle.Utilities.Encoders
{
	/**
	* Convert binary data to and from UrlBase64 encoding.  This is identical to
	* Base64 encoding, except that the padding character is "." and the other 
	* non-alphanumeric characters are "-" and "_" instead of "+" and "/".
	* <p>
	* The purpose of UrlBase64 encoding is to provide a compact encoding of binary
	* data that is safe for use as an URL parameter. Base64 encoding does not
	* produce encoded values that are safe for use in URLs, since "/" can be 
	* interpreted as a path delimiter; "+" is the encoded form of a space; and
	* "=" is used to separate a name from the corresponding value in an URL 
	* parameter.
	* </p>
	*/
	public class UrlBase64Encoder
		: Base64Encoder
	{
		public UrlBase64Encoder()
		{
			encodingTable[encodingTable.Length - 2] = (byte) '-';
			encodingTable[encodingTable.Length - 1] = (byte) '_';
			padding = (byte) '.';
			// we must re-create the decoding table with the new encoded values.
			InitialiseDecodingTable();
		}
	}
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/encoders/UrlBase64Encoder.cs`.

**Classes defined**: UrlBase64Encoder

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 29
- Comment lines: 14
- Blank lines: -12

### Main Components

**Classes** (1):
- `UrlBase64Encoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `.` (imported)



## Testing & Execution

**To execute this C# file:**

