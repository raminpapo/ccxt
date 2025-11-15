# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/AsymmetricKeyParameter.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/AsymmetricKeyParameter.cs`
- **Size**: 815 bytes
- **Lines**: 48
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Crypto;

namespace Org.BouncyCastle.Crypto
{
    public abstract class AsymmetricKeyParameter
		: ICipherParameters
    {
        private readonly bool privateKey;

        protected AsymmetricKeyParameter(
            bool privateKey)
        {
            this.privateKey = privateKey;
        }

		public bool IsPrivate
        {
            get { return privateKey; }
        }

		public override bool Equals(
			object obj)
		{
			AsymmetricKeyParameter other = obj as AsymmetricKeyParameter;

			if (other == null)
			{
				return false;
			}

			return Equals(other);
		}

		protected bool Equals(
			AsymmetricKeyParameter other)
		{
			return privateKey == other.privateKey;
		}

		public override int GetHashCode()
		{
			return privateKey.GetHashCode();
		}
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/AsymmetricKeyParameter.cs`.

**Classes defined**: AsymmetricKeyParameter



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 38
- Comment lines: 0
- Blank lines: 10

### Main Components

**Classes** (1):
- `AsymmetricKeyParameter`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

