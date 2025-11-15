# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AlgorithmIdentifier.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AlgorithmIdentifier.cs`
- **Size**: 2,478 bytes
- **Lines**: 84
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.X509
{
    public class AlgorithmIdentifier
        : Asn1Encodable
    {
        private readonly DerObjectIdentifier	algorithm;
        private readonly Asn1Encodable			parameters;

        public static AlgorithmIdentifier GetInstance(
            Asn1TaggedObject	obj,
            bool				explicitly)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, explicitly));
        }

        public static AlgorithmIdentifier GetInstance(
            object obj)
        {
            if (obj == null)
                return null;
            if (obj is AlgorithmIdentifier)
                return (AlgorithmIdentifier)obj;
            return new AlgorithmIdentifier(Asn1Sequence.GetInstance(obj));
        }

        public AlgorithmIdentifier(
            DerObjectIdentifier algorithm)
        {
            this.algorithm = algorithm;
        }

        public AlgorithmIdentifier(
            DerObjectIdentifier algorithm,
            Asn1Encodable		parameters)
        {
            this.algorithm = algorithm;
            this.parameters = parameters;
        }

        internal AlgorithmIdentifier(
            Asn1Sequence seq)
        {
            if (seq.Count < 1 || seq.Count > 2)
                throw new ArgumentException("Bad sequence size: " + seq.Count);

            this.algorithm = DerObjectIdentifier.GetInstance(seq[0]);
            this.parameters = seq.Count < 2 ? null : seq[1];
        }

        /// <summary>
        /// Return the OID in the Algorithm entry of this identifier.
        /// </summary>
		public virtual DerObjectIdentifier Algorithm
		{
			get { return algorithm; }
		}

        /// <summary>
        /// Return the parameters structure in the Parameters entry of this identifier.
        /// </summary>
        public virtual Asn1Encodable Parameters
        {
            get { return parameters; }
        }

        /**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         *      AlgorithmIdentifier ::= Sequence {
         *                            algorithm OBJECT IDENTIFIER,
         *                            parameters ANY DEFINED BY algorithm OPTIONAL }
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
            Asn1EncodableVector v = new Asn1EncodableVector(algorithm);
            v.AddOptional(parameters);
            return new DerSequence(v);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AlgorithmIdentifier.cs`.

**Classes defined**: AlgorithmIdentifier

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 84
- Code lines: 67
- Comment lines: 14
- Blank lines: 3

### Main Components

**Classes** (1):
- `AlgorithmIdentifier`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

