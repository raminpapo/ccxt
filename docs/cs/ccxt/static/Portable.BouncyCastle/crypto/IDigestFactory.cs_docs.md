# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IDigestFactory.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IDigestFactory.cs`
- **Size**: 955 bytes
- **Lines**: 26
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Base interface for operator factories that create stream-based digest calculators.
    /// </summary>   
    public interface IDigestFactory
	{
		/// <summary>The algorithm details object for calculators made by this factory.</summary>
		object AlgorithmDetails { get ; }

		/// <summary>Return the size of the digest associated with this factory.</summary>
		/// <returns>The length of the digest produced by this calculators from this factory in bytes.</returns>
		int DigestLength { get; }

		/// <summary>
		/// Create a stream calculator for the digest associated with this factory. The stream
		/// calculator is used for the actual operation of entering the data to be digested
		/// and producing the digest block.
		/// </summary>
		/// <returns>A calculator producing an IBlockResult with the final digest in it.</returns>
		IStreamCalculator CreateCalculator();
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IDigestFactory.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 10
- Comment lines: 12
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

