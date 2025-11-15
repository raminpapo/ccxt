# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/encoders/Base64.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/encoders/Base64.cs`
- **Size**: 3,308 bytes
- **Lines**: 121
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.IO;
using System.Text;

namespace Org.BouncyCastle.Utilities.Encoders
{
    public sealed class Base64
    {
        private Base64()
        {
        }

        public static string ToBase64String(
            byte[] data)
        {
            return Convert.ToBase64String(data, 0, data.Length);
        }

        public static string ToBase64String(
            byte[] data,
            int off,
            int length)
        {
            return Convert.ToBase64String(data, off, length);
        }

        /**
         * encode the input data producing a base 64 encoded byte array.
         *
         * @return a byte array containing the base 64 encoded data.
         */
        public static byte[] Encode(
            byte[] data)
        {
            return Encode(data, 0, data.Length);
        }

        /**
         * encode the input data producing a base 64 encoded byte array.
         *
         * @return a byte array containing the base 64 encoded data.
         */
        public static byte[] Encode(
            byte[] data,
            int off,
            int length)
        {
            string s = Convert.ToBase64String(data, off, length);
            return Strings.ToAsciiByteArray(s);
        }

        /**
         * Encode the byte data to base 64 writing it to the given output stream.
         *
         * @return the number of bytes produced.
         */
        public static int Encode(
            byte[]	data,
            Stream	outStream)
        {
            byte[] encoded = Encode(data);
            outStream.Write(encoded, 0, encoded.Length);
            return encoded.Length;
        }

        /**
         * Encode the byte data to base 64 writing it to the given output stream.
         *
         * @return the number of bytes produced.
         */
        public static int Encode(
            byte[]	data,
            int		off,
            int		length,
            Stream	outStream)
        {
            byte[] encoded = Encode(data, off, length);
            outStream.Write(encoded, 0, encoded.Length);
            return encoded.Length;
        }

        /**
         * decode the base 64 encoded input data. It is assumed the input data is valid.
         *
         * @return a byte array representing the decoded data.
         */
        public static byte[] Decode(
            byte[] data)
        {
            string s = Strings.FromAsciiByteArray(data);
            return Convert.FromBase64String(s);
        }

        /**
         * decode the base 64 encoded string data - whitespace will be ignored.
         *
         * @return a byte array representing the decoded data.
         */
        public static byte[] Decode(
            string data)
        {
            return Convert.FromBase64String(data);
        }

        /**
         * decode the base 64 encoded string data writing it to the given output stream,
         * whitespace characters will be ignored.
         *
         * @return the number of bytes produced.
         */
        public static int Decode(
            string	data,
            Stream	outStream)
        {
            byte[] decoded = Decode(data);
            outStream.Write(decoded, 0, decoded.Length);
            return decoded.Length;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/encoders/Base64.cs`.

**Classes defined**: Base64

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 121
- Code lines: 110
- Comment lines: 36
- Blank lines: -25

### Main Components

**Classes** (1):
- `Base64`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

