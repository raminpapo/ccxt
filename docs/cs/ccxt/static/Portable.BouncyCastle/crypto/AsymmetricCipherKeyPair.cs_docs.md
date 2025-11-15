# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/AsymmetricCipherKeyPair.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/AsymmetricCipherKeyPair.cs`
- **Size**: 1,466 bytes
- **Lines**: 53
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto
{
    /**
     * a holding class for public/private parameter pairs.
     */
    public class AsymmetricCipherKeyPair
    {
        private readonly AsymmetricKeyParameter publicParameter;
        private readonly AsymmetricKeyParameter privateParameter;

		/**
         * basic constructor.
         *
         * @param publicParam a public key parameters object.
         * @param privateParam the corresponding private key parameters.
         */
        public AsymmetricCipherKeyPair(
            AsymmetricKeyParameter    publicParameter,
            AsymmetricKeyParameter    privateParameter)
        {
			if (publicParameter.IsPrivate)
				throw new ArgumentException("Expected a public key", "publicParameter");
			if (!privateParameter.IsPrivate)
				throw new ArgumentException("Expected a private key", "privateParameter");

			this.publicParameter = publicParameter;
            this.privateParameter = privateParameter;
        }

		/**
         * return the public key parameters.
         *
         * @return the public key parameters.
         */
        public AsymmetricKeyParameter Public
        {
            get { return publicParameter; }
        }

		/**
         * return the private key parameters.
         *
         * @return the private key parameters.
         */
        public AsymmetricKeyParameter Private
        {
            get { return privateParameter; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/AsymmetricCipherKeyPair.cs`.

**Classes defined**: for, AsymmetricCipherKeyPair

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 47
- Comment lines: 19
- Blank lines: -13

### Main Components

**Classes** (1):
- `AsymmetricCipherKeyPair`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

