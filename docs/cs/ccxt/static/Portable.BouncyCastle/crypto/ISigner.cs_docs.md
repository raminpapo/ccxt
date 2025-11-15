# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/ISigner.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/ISigner.cs`
- **Size**: 2,050 bytes
- **Lines**: 46
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto
{
    public interface ISigner
    {
        /// <summary>The algorithm name.</summary>
        string AlgorithmName { get; }

        /// <summary>Initialise the signer for signing or verification.</summary>
        /// <param name="forSigning">true if for signing, false otherwise.</param>
        /// <param name="parameters">necessary parameters.</param>
        void Init(bool forSigning, ICipherParameters parameters);

        /// <summary>Update the signer with a single byte.</summary>
        /// <param name="input">the input byte to be entered.</param>
        void Update(byte input);

        /// <summary>Update the signer with a block of bytes.</summary>
        /// <param name="input">the byte array containing the data.</param>
        /// <param name="inOff">the offset into the byte array where the data starts.</param>
        /// <param name="inLen">the length of the data.</param>
        void BlockUpdate(byte[] input, int inOff, int inLen);

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        /// <summary>Update the signer with a span of bytes.</summary>
        /// <param name="input">the span containing the data.</param>
        void BlockUpdate(ReadOnlySpan<byte> input);
#endif

        /// <summary>Generate a signature for the message we've been loaded with using the key we were initialised with.
        /// </summary>
        /// <returns>A byte array containing the signature for the message.</returns>
        byte[] GenerateSignature();

        /// <summary>Return true if the internal state represents the signature described in the passed in array.
        /// </summary>
        /// <param name="signature">an array containing the candidate signature to verify.</param>
        /// <returns>true if the internal state represents the signature described in the passed in array.</returns>
        bool VerifySignature(byte[] signature);

        /// <summary>Reset the signer back to its initial state.</summary>
        void Reset();
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/ISigner.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 15
- Comment lines: 22
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

