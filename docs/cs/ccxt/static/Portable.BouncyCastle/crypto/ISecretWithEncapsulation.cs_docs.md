# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/ISecretWithEncapsulation.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/ISecretWithEncapsulation.cs`
- **Size**: 572 bytes
- **Lines**: 21
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto
{
    public interface ISecretWithEncapsulation
        : IDisposable 
    {
        
        ///<summary>
        /// Return the secret associated with the encapsulation.
        /// </summary>
        /// <returns> the secret the encapsulation is for.</returns>
        byte[] GetSecret();

        /// <summary>
        /// Return the data that carries the secret in its encapsulated form.
        /// </summary>
        /// <returns> the encapsulation of the secret.</returns>
        byte[] GetEncapsulation();
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/ISecretWithEncapsulation.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 10
- Comment lines: 8
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

