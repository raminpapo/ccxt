# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/CipherKeyGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/CipherKeyGenerator.cs`
- **Size**: 1,726 bytes
- **Lines**: 84
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto
{
	/**
	 * The base class for symmetric, or secret, cipher key generators.
	 */
	public class CipherKeyGenerator
	{
		protected internal SecureRandom	random;
		protected internal int			strength;
		private bool uninitialised = true;
		private int defaultStrength;

		public CipherKeyGenerator()
		{
		}

		internal CipherKeyGenerator(
			int defaultStrength)
		{
			if (defaultStrength < 1)
				throw new ArgumentException("strength must be a positive value", "defaultStrength");

			this.defaultStrength = defaultStrength;
		}

		public int DefaultStrength
		{
			get { return defaultStrength; }
		}

		/**
		 * initialise the key generator.
		 *
		 * @param param the parameters to be used for key generation
		 */
		public void Init(
			KeyGenerationParameters parameters)
		{
			if (parameters == null)
				throw new ArgumentNullException("parameters");

			this.uninitialised = false;

			engineInit(parameters);
		}

		protected virtual void engineInit(
			KeyGenerationParameters parameters)
		{
			this.random = parameters.Random;
			this.strength = (parameters.Strength + 7) / 8;
		}

		/**
		 * Generate a secret key.
		 *
		 * @return a byte array containing the key value.
		 */
		public byte[] GenerateKey()
		{
			if (uninitialised)
			{
				if (defaultStrength < 1)
					throw new InvalidOperationException("Generator has not been initialised");

				uninitialised = false;

				engineInit(new KeyGenerationParameters(new SecureRandom(), defaultStrength));
			}

			return engineGenerateKey();
		}

        protected virtual byte[] engineGenerateKey()
		{
            return SecureRandom.GetNextBytes(random, strength);
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/CipherKeyGenerator.cs`.

**Classes defined**: for, CipherKeyGenerator

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 84
- Code lines: 68
- Comment lines: 13
- Blank lines: 3

### Main Components

**Classes** (1):
- `CipherKeyGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

