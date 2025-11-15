# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECKeyGenerationParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECKeyGenerationParameters.cs`
- **Size**: 1,009 bytes
- **Lines**: 42
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Asn1;
// using Org.BouncyCastle.Asn1.CryptoPro;
using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class ECKeyGenerationParameters
		: KeyGenerationParameters
    {
        private readonly ECDomainParameters domainParams;
		private readonly DerObjectIdentifier publicKeyParamSet;

		public ECKeyGenerationParameters(
			ECDomainParameters	domainParameters,
			SecureRandom		random)
			: base(random, domainParameters.N.BitLength)
        {
            this.domainParams = domainParameters;
        }

		public ECKeyGenerationParameters(
			DerObjectIdentifier	publicKeyParamSet,
			SecureRandom		random)
			: this(ECKeyParameters.LookupParameters(publicKeyParamSet), random)
		{
			this.publicKeyParamSet = publicKeyParamSet;
		}

		public ECDomainParameters DomainParameters
        {
			get { return domainParams; }
        }

		public DerObjectIdentifier PublicKeyParamSet
		{
			get { return publicKeyParamSet; }
		}
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECKeyGenerationParameters.cs`.

**Classes defined**: ECKeyGenerationParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 34
- Comment lines: 1
- Blank lines: 7

### Main Components

**Classes** (1):
- `ECKeyGenerationParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

