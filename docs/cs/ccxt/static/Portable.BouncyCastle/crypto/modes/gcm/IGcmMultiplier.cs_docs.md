# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/IGcmMultiplier.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/IGcmMultiplier.cs`
- **Size**: 153 bytes
- **Lines**: 11
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto.Modes.Gcm
{
	public interface IGcmMultiplier
	{
		void Init(byte[] H);
		void MultiplyH(byte[] x);
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/IGcmMultiplier.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 11
- Code lines: 9
- Comment lines: 0
- Blank lines: 2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

