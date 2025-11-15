# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/WNafPreCompInfo.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/WNafPreCompInfo.cs`
- **Size**: 2,196 bytes
- **Lines**: 86
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Math.EC.Multiplier
{
    /**
    * Class holding precomputation data for the WNAF (Window Non-Adjacent Form)
    * algorithm.
    */
    public class WNafPreCompInfo
        : PreCompInfo
    {
        internal volatile int m_promotionCountdown = 4;

        protected int m_confWidth = -1;

        /**
         * Array holding the precomputed <code>ECPoint</code>s used for a Window
         * NAF multiplication.
         */
        protected ECPoint[] m_preComp = null;

        /**
         * Array holding the negations of the precomputed <code>ECPoint</code>s used
         * for a Window NAF multiplication.
         */
        protected ECPoint[] m_preCompNeg = null;

        /**
         * Holds an <code>ECPoint</code> representing Twice(this). Used for the
         * Window NAF multiplication to create or extend the precomputed values.
         */
        protected ECPoint m_twice = null;

        protected int m_width = -1;

        internal int DecrementPromotionCountdown()
        {
            int t = m_promotionCountdown;
            if (t > 0)
            {
                m_promotionCountdown = --t;
            }
            return t;
        }

        internal int PromotionCountdown
        {
            get { return m_promotionCountdown; }
            set { this.m_promotionCountdown = value; }
        }

        public virtual bool IsPromoted
        {
            get { return m_promotionCountdown <= 0; }
        }

        public virtual int ConfWidth
        {
            get { return m_confWidth; }
            set { this.m_confWidth = value; }
        }

        public virtual ECPoint[] PreComp
        {
            get { return m_preComp; }
            set { this.m_preComp = value; }
        }

        public virtual ECPoint[] PreCompNeg
        {
            get { return m_preCompNeg; }
            set { this.m_preCompNeg = value; }
        }

        public virtual ECPoint Twice
        {
            get { return m_twice; }
            set { this.m_twice = value; }
        }

        public virtual int Width
        {
            get { return m_width; }
            set { this.m_width = value; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/WNafPreCompInfo.cs`.

**Classes defined**: WNafPreCompInfo

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 86
- Code lines: 72
- Comment lines: 16
- Blank lines: -2

### Main Components

**Classes** (1):
- `WNafPreCompInfo`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

