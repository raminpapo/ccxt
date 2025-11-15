# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/KeyParameter.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/KeyParameter.cs`
- **Size**: 907 bytes
- **Lines**: 44
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Crypto;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class KeyParameter
		: ICipherParameters
    {
        private readonly byte[] key;

		public KeyParameter(
			byte[] key)
		{
			if (key == null)
				throw new ArgumentNullException("key");

			this.key = (byte[]) key.Clone();
		}

		public KeyParameter(
            byte[]	key,
            int		keyOff,
            int		keyLen)
        {
			if (key == null)
				throw new ArgumentNullException("key");
			if (keyOff < 0 || keyOff > key.Length)
				throw new ArgumentOutOfRangeException("keyOff");
            if (keyLen < 0 || keyLen > (key.Length - keyOff))
				throw new ArgumentOutOfRangeException("keyLen");

			this.key = new byte[keyLen];
            Array.Copy(key, keyOff, this.key, 0, keyLen);
        }

		public byte[] GetKey()
        {
			return (byte[]) key.Clone();
        }
    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/KeyParameter.cs`.

**Classes defined**: KeyParameter



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 35
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `KeyParameter`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

