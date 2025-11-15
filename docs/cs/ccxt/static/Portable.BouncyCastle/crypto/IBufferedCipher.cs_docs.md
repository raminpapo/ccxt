# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IBufferedCipher.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IBufferedCipher.cs`
- **Size**: 1,949 bytes
- **Lines**: 58
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto
{
	/// <remarks>Block cipher engines are expected to conform to this interface.</remarks>
    public interface IBufferedCipher
    {
		/// <summary>The name of the algorithm this cipher implements.</summary>
		string AlgorithmName { get; }

		/// <summary>Initialise the cipher.</summary>
		/// <param name="forEncryption">If true the cipher is initialised for encryption,
		/// if false for decryption.</param>
		/// <param name="parameters">The key and other data required by the cipher.</param>
        void Init(bool forEncryption, ICipherParameters parameters);

		int GetBlockSize();

		int GetOutputSize(int inputLen);

		int GetUpdateOutputSize(int inputLen);

		byte[] ProcessByte(byte input);
		int ProcessByte(byte input, byte[] output, int outOff);

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        int ProcessByte(byte input, Span<byte> output);
#endif

        byte[] ProcessBytes(byte[] input);
		byte[] ProcessBytes(byte[] input, int inOff, int length);
		int ProcessBytes(byte[] input, byte[] output, int outOff);
		int ProcessBytes(byte[] input, int inOff, int length, byte[] output, int outOff);

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
		int ProcessBytes(ReadOnlySpan<byte> input, Span<byte> output);
#endif

		byte[] DoFinal();
		byte[] DoFinal(byte[] input);
		byte[] DoFinal(byte[] input, int inOff, int length);
		int DoFinal(byte[] output, int outOff);
		int DoFinal(byte[] input, byte[] output, int outOff);
		int DoFinal(byte[] input, int inOff, int length, byte[] output, int outOff);

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
		int DoFinal(Span<byte> output);
		int DoFinal(ReadOnlySpan<byte> input, Span<byte> output);
#endif

		/// <summary>
		/// Reset the cipher. After resetting the cipher is in the same state
		/// as it was after the last init (if there was one).
		/// </summary>
        void Reset();
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IBufferedCipher.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 29
- Comment lines: 16
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

