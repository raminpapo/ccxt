# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/signers/GenericSigner.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/signers/GenericSigner.cs`
- **Size**: 3,579 bytes
- **Lines**: 124
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Crypto.Parameters;
using Org.BouncyCastle.Security;
using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Crypto.Signers
{
    public class GenericSigner
        : ISigner
    {
        private readonly IAsymmetricBlockCipher engine;
        private readonly IDigest digest;
        private bool forSigning;

        public GenericSigner(
            IAsymmetricBlockCipher	engine,
            IDigest					digest)
        {
            this.engine = engine;
            this.digest = digest;
        }

        public virtual string AlgorithmName
        {
            get { return "Generic(" + engine.AlgorithmName + "/" + digest.AlgorithmName + ")"; }
        }

        /**
        * initialise the signer for signing or verification.
        *
        * @param forSigning
        *            true if for signing, false otherwise
        * @param parameters
        *            necessary parameters.
        */
        public virtual void Init(bool forSigning, ICipherParameters parameters)
        {
            this.forSigning = forSigning;

            AsymmetricKeyParameter k;
            if (parameters is ParametersWithRandom)
            {
                k = (AsymmetricKeyParameter)((ParametersWithRandom)parameters).Parameters;
            }
            else
            {
                k = (AsymmetricKeyParameter)parameters;
            }

            if (forSigning && !k.IsPrivate)
                throw new InvalidKeyException("Signing requires private key.");

            if (!forSigning && k.IsPrivate)
                throw new InvalidKeyException("Verification requires public key.");

            Reset();

            engine.Init(forSigning, parameters);
        }

        public virtual void Update(byte input)
        {
            digest.Update(input);
        }

        public virtual void BlockUpdate(byte[] input, int inOff, int inLen)
        {
            digest.BlockUpdate(input, inOff, inLen);
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public virtual void BlockUpdate(ReadOnlySpan<byte> input)
        {
            digest.BlockUpdate(input);
        }
#endif

        public virtual byte[] GenerateSignature()
        {
            if (!forSigning)
                throw new InvalidOperationException("GenericSigner not initialised for signature generation.");

            byte[] hash = new byte[digest.GetDigestSize()];
            digest.DoFinal(hash, 0);

            return engine.ProcessBlock(hash, 0, hash.Length);
        }

        public virtual bool VerifySignature(byte[] signature)
        {
            if (forSigning)
                throw new InvalidOperationException("GenericSigner not initialised for verification");

            byte[] hash = new byte[digest.GetDigestSize()];
            digest.DoFinal(hash, 0);

            try
            {
                byte[] sig = engine.ProcessBlock(signature, 0, signature.Length);

                // Extend with leading zeroes to match the digest size, if necessary.
                if (sig.Length < hash.Length)
                {
                    byte[] tmp = new byte[hash.Length];
                    Array.Copy(sig, 0, tmp, tmp.Length - sig.Length, sig.Length);
                    sig = tmp;
                }

                return Arrays.ConstantTimeAreEqual(sig, hash);
            }
            catch (Exception)
            {
                return false;
            }
        }

        public virtual void Reset()
        {
            digest.Reset();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/signers/GenericSigner.cs`.

**Classes defined**: GenericSigner

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 124
- Code lines: 98
- Comment lines: 11
- Blank lines: 15

### Main Components

**Classes** (1):
- `GenericSigner`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

