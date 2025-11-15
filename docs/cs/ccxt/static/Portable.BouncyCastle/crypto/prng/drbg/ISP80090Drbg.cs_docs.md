# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/prng/drbg/ISP80090Drbg.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/drbg/ISP80090Drbg.cs`
- **Size**: 1,191 bytes
- **Lines**: 40
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto.Prng.Drbg
{
	/**
	 * Interface to SP800-90A deterministic random bit generators.
	 */
	public interface ISP80090Drbg
	{
	    /**
	     * Return the block size of the DRBG.
	     *
	     * @return the block size (in bits) produced by each round of the DRBG.
	     */
		int BlockSize { get; }

        /**
	     * Populate a passed in array with random data.
	     *
	     * @param output output array for generated bits.
	     * @param additionalInput additional input to be added to the DRBG in this step.
	     * @param predictionResistant true if a reseed should be forced, false otherwise.
	     *
	     * @return number of bits generated, -1 if a reseed required.
	     */
        int Generate(byte[] output, int outputOff, int outputLen, byte[] additionalInput, bool predictionResistant);

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        int Generate(Span<byte> output, byte[] additionalInput, bool predictionResistant);
#endif

        /**
	     * Reseed the DRBG.
	     *
	     * @param additionalInput additional input to be added to the DRBG in this step.
	     */
        void Reseed(byte[] additionalInput);
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/drbg/ISP80090Drbg.cs`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 33
- Comment lines: 24
- Blank lines: -17

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

