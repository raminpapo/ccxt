# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/IntType.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/IntType.cs`
- **Size**: 2,488 bytes
- **Lines**: 80
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Numerics;
using Nethereum.ABI.Decoders;
using Nethereum.ABI.Encoders;

namespace Nethereum.ABI
{
    public class IntType : ABIType
    {
        public static BigInteger MAX_INT256_VALUE =
            BigInteger.Parse("57896044618658097711785492504343953926634992332820282019728792003956564819967");
        
        public static BigInteger MIN_INT256_VALUE =
            BigInteger.Parse("-57896044618658097711785492504343953926634992332820282019728792003956564819968");

        public static BigInteger MAX_UINT256_VALUE =
            BigInteger.Parse("115792089237316195423570985008687907853269984665640564039457584007913129639935");

        public static BigInteger MIN_UINT_VALUE = 0;

        public IntType(string name) : base(name)
        {
            Decoder = new IntTypeDecoder(IsSigned(CanonicalName));
            Encoder = new IntTypeEncoder(IsSigned(CanonicalName), GetSize(CanonicalName));
        }

        public override string CanonicalName
        {
            get
            {
                if (Name.Equals("int"))
                    return "int256";
                if (Name.Equals("uint"))
                    return "uint256";
                return base.CanonicalName;
            }
        }

        private static bool IsSigned(string name)
        {
            return !name.ToLower().StartsWith("u");
        }

        public static BigInteger GetMaxSignedValue(uint size)
        {
            CheckIsValidAndThrow(size);
            return BigInteger.Pow(2, (int) size - 1) - 1;
        }

        public static BigInteger GetMinSignedValue(uint size)
        {
            CheckIsValidAndThrow(size);
            return BigInteger.Pow(-2, (int) size - 1);
        }

        public static BigInteger GetMaxUnSignedValue(uint size)
        {
            CheckIsValidAndThrow(size);
            return BigInteger.Pow(2, (int) size) - 1;
        }

        private static void CheckIsValidAndThrow(uint size)
        {
            if (!IsValidSize(size)) throw new ArgumentException("Invalid size for type int :" + size);
        }

        public static bool IsValidSize(uint size)
        {
            var divisible = size % 8 == 0;
            return divisible && size <= 256 && size >= 8;
        }

        private static uint GetSize(string name)
        {
            if (IsSigned(name))
                return uint.Parse(name.Substring(3));
            return uint.Parse(name.Substring(4));
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/IntType.cs`.

**Classes defined**: IntType



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 67
- Comment lines: 0
- Blank lines: 13

### Main Components

**Classes** (1):
- `IntType`

**Constants** (4):
- `MAX_INT256_VALUE`
- `MAX_UINT256_VALUE`
- `MIN_INT256_VALUE`
- `MIN_UINT_VALUE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

