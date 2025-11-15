# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/prng/IRandomGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/IRandomGenerator.cs`
- **Size**: 1,097 bytes
- **Lines**: 31
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto.Prng
{
	/// <remarks>Generic interface for objects generating random bytes.</remarks>
	public interface IRandomGenerator
	{
		/// <summary>Add more seed material to the generator.</summary>
		/// <param name="seed">A byte array to be mixed into the generator's state.</param>
		void AddSeedMaterial(byte[] seed);

		/// <summary>Add more seed material to the generator.</summary>
		/// <param name="seed">A long value to be mixed into the generator's state.</param>
		void AddSeedMaterial(long seed);

		/// <summary>Fill byte array with random values.</summary>
		/// <param name="bytes">Array to be filled.</param>
		void NextBytes(byte[] bytes);

		/// <summary>Fill byte array with random values.</summary>
		/// <param name="bytes">Array to receive bytes.</param>
		/// <param name="start">Index to start filling at.</param>
		/// <param name="len">Length of segment to fill.</param>
		void NextBytes(byte[] bytes, int start, int len);

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
		void NextBytes(Span<byte> bytes);
#endif
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/prng/IRandomGenerator.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 12
- Comment lines: 13
- Blank lines: 6

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

