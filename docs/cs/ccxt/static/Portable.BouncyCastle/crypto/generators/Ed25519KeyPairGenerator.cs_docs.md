# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/generators/Ed25519KeyPairGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/generators/Ed25519KeyPairGenerator.cs`
- **Size**: 746 bytes
- **Lines**: 26
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Crypto.Parameters;
using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto.Generators
{
    public class Ed25519KeyPairGenerator
        : IAsymmetricCipherKeyPairGenerator
    {
        private SecureRandom random;

        public virtual void Init(KeyGenerationParameters parameters)
        {
            this.random = parameters.Random;
        }

        public virtual AsymmetricCipherKeyPair GenerateKeyPair()
        {
            Ed25519PrivateKeyParameters privateKey = new Ed25519PrivateKeyParameters(random);
            Ed25519PublicKeyParameters publicKey = privateKey.GeneratePublicKey();
            return new AsymmetricCipherKeyPair(publicKey, privateKey);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/generators/Ed25519KeyPairGenerator.cs`.

**Classes defined**: Ed25519KeyPairGenerator



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 21
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (1):
- `Ed25519KeyPairGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

