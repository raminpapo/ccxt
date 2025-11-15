# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IWrapper.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IWrapper.cs`
- **Size**: 412 bytes
- **Lines**: 19
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Security;

namespace Org.BouncyCastle.Crypto
{
    public interface IWrapper
    {
		/// <summary>The name of the algorithm this cipher implements.</summary>
		string AlgorithmName { get; }

		void Init(bool forWrapping, ICipherParameters parameters);

		byte[] Wrap(byte[] input, int inOff, int length);

        byte[] Unwrap(byte[] input, int inOff, int length);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IWrapper.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 12
- Comment lines: 1
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

