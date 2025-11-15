# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/OidTokenizer.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/OidTokenizer.cs`
- **Size**: 1,027 bytes
- **Lines**: 46
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Asn1
{
    /**
     * class for breaking up an Oid into it's component tokens, ala
     * java.util.StringTokenizer. We need this class as some of the
     * lightweight Java environment don't support classes like
     * StringTokenizer.
     */
    public class OidTokenizer
    {
        private string  oid;
        private int     index;

		public OidTokenizer(
            string oid)
        {
            this.oid = oid;
        }

		public bool HasMoreTokens
        {
			get { return index != -1; }
        }

		public string NextToken()
        {
            if (index == -1)
            {
                return null;
            }

            int end = oid.IndexOf('.', index);
            if (end == -1)
            {
                string lastToken = oid.Substring(index);
                index = -1;
                return lastToken;
            }

            string nextToken = oid.Substring(index, end - index);
			index = end + 1;
            return nextToken;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/OidTokenizer.cs`.

**Classes defined**: OidTokenizer, as, for

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 40
- Comment lines: 6
- Blank lines: 0

### Main Components

**Classes** (1):
- `OidTokenizer`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

