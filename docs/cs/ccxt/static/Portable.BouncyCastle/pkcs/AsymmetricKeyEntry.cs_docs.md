# Documentation: cs/ccxt/static/Portable.BouncyCastle/pkcs/AsymmetricKeyEntry.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/pkcs/AsymmetricKeyEntry.cs`
- **Size**: 1,080 bytes
- **Lines**: 47
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
// using System.Collections.Generic;

// using Org.BouncyCastle.Asn1;
// using Org.BouncyCastle.Crypto;

// namespace Org.BouncyCastle.Pkcs
// {
//     public class AsymmetricKeyEntry
//         : Pkcs12Entry
//     {
//         private readonly AsymmetricKeyParameter key;

// 		public AsymmetricKeyEntry(AsymmetricKeyParameter key)
// 			: base(new Dictionary<DerObjectIdentifier, Asn1Encodable>())
//         {
//             this.key = key;
//         }

//         public AsymmetricKeyEntry(AsymmetricKeyParameter key,
// 			IDictionary<DerObjectIdentifier, Asn1Encodable> attributes)
// 			: base(attributes)
//         {
//             this.key = key;
//         }

// 		public AsymmetricKeyParameter Key
//         {
//             get { return this.key; }
//         }

// 		public override bool Equals(object obj)
// 		{
// 			AsymmetricKeyEntry other = obj as AsymmetricKeyEntry;

// 			if (other == null)
// 				return false;

// 			return key.Equals(other.key);
// 		}

// 		public override int GetHashCode()
// 		{
// 			return ~key.GetHashCode();
// 		}
// 	}
// }

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/pkcs/AsymmetricKeyEntry.cs`.

**Classes defined**: AsymmetricKeyEntry



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 0
- Comment lines: 37
- Blank lines: 10

### Main Components

**Classes** (1):
- `AsymmetricKeyEntry`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

