# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithSBox.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithSBox.cs`
- **Size**: 474 bytes
- **Lines**: 25
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Crypto;

namespace Org.BouncyCastle.Crypto.Parameters
{
	public class ParametersWithSBox : ICipherParameters
	{
		private ICipherParameters  parameters;
		private byte[] sBox;

		public ParametersWithSBox(
			ICipherParameters parameters,
			byte[] sBox)
		{
			this.parameters = parameters;
			this.sBox = sBox;
		}

		public byte[] GetSBox() { return sBox; }

		public ICipherParameters Parameters { get { return parameters; } }
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ParametersWithSBox.cs`.

**Classes defined**: ParametersWithSBox



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 19
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `ParametersWithSBox`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

