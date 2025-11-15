# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IEntropySource.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IEntropySource.cs`
- **Size**: 787 bytes
- **Lines**: 30
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Crypto
{
	/// <summary>
	/// Base interface describing an entropy source for a DRBG.
	/// </summary>
	public interface IEntropySource
	{
		/// <summary>
		/// Return whether or not this entropy source is regarded as prediction resistant.
		/// </summary>
		/// <value><c>true</c> if this instance is prediction resistant; otherwise, <c>false</c>.</value>
		bool IsPredictionResistant { get; }

		/// <summary>
		/// Return a byte array of entropy.
		/// </summary>
		/// <returns>The entropy bytes.</returns>
		byte[] GetEntropy();

		/// <summary>
		/// Return the number of bits of entropy this source can produce.
		/// </summary>
		/// <value>The size, in bits, of the return value of getEntropy.</value>
		int EntropySize { get; }
	}
}


```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IEntropySource.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 10
- Comment lines: 15
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

