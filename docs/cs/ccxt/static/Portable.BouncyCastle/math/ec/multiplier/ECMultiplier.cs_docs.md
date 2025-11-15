# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/ECMultiplier.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/ECMultiplier.cs`
- **Size**: 631 bytes
- **Lines**: 19
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Math.EC.Multiplier
{
    /**
    * Interface for classes encapsulating a point multiplication algorithm
    * for <code>ECPoint</code>s.
    */
    public interface ECMultiplier
    {
        /**
         * Multiplies the <code>ECPoint p</code> by <code>k</code>, i.e.
         * <code>p</code> is added <code>k</code> times to itself.
         * @param p The <code>ECPoint</code> to be multiplied.
         * @param k The factor by which <code>p</code> is multiplied.
         * @return <code>p</code> multiplied by <code>k</code>.
         */
        ECPoint Multiply(ECPoint p, BigInteger k);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/ECMultiplier.cs`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 18
- Comment lines: 11
- Blank lines: -10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

