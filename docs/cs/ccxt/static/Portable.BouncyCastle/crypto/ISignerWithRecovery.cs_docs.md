# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/ISignerWithRecovery.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/ISignerWithRecovery.cs`
- **Size**: 1,080 bytes
- **Lines**: 38
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Text;

namespace Org.BouncyCastle.Crypto
{
    /**
     * Signer with message recovery.
     */
    public interface ISignerWithRecovery
        : ISigner
    {
        /**
         * Returns true if the signer has recovered the full message as
         * part of signature verification.
         *
         * @return true if full message recovered.
         */
        bool HasFullMessage();

        /**
         * Returns a reference to what message was recovered (if any).
         *
         * @return full/partial message, null if nothing.
         */
        byte[] GetRecoveredMessage();

		/**
		 * Perform an update with the recovered message before adding any other data. This must
		 * be the first update method called, and calling it will result in the signer assuming
		 * that further calls to update will include message content past what is recoverable.
		 *
		 * @param signature the signature that we are in the process of verifying.
		 * @throws IllegalStateException
		 */
		void UpdateWithRecoveredMessage(byte[] signature);
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/ISignerWithRecovery.cs`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 34
- Comment lines: 22
- Blank lines: -18

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

