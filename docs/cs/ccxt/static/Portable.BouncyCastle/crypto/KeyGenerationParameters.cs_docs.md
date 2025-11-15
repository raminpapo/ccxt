# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/KeyGenerationParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/KeyGenerationParameters.cs`
- **Size**: 1,418 bytes
- **Lines**: 56
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto
{
    /**
     * The base class for parameters to key generators.
     */
    public class KeyGenerationParameters
    {
        private SecureRandom	random;
        private int				strength;

        /**
         * initialise the generator with a source of randomness
         * and a strength (in bits).
         *
         * @param random the random byte source.
         * @param strength the size, in bits, of the keys we want to produce.
         */
        public KeyGenerationParameters(
            SecureRandom	random,
            int				strength)
        {
			if (random == null)
				throw new ArgumentNullException("random");
			if (strength < 1)
				throw new ArgumentException("strength must be a positive value", "strength");

			this.random = random;
            this.strength = strength;
        }

		/**
         * return the random source associated with this
         * generator.
         *
         * @return the generators random source.
         */
        public SecureRandom Random
        {
            get { return random; }
        }

		/**
         * return the bit strength for keys produced by this generator,
         *
         * @return the strength of the keys this generator produces (in bits).
         */
        public int Strength
        {
            get { return strength; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/KeyGenerationParameters.cs`.

**Classes defined**: KeyGenerationParameters, for

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 50
- Comment lines: 21
- Blank lines: -15

### Main Components

**Classes** (1):
- `KeyGenerationParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

