# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/LazyDLEnumerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/LazyDLEnumerator.cs`
- **Size**: 1,409 bytes
- **Lines**: 66
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;
using System.IO;

namespace Org.BouncyCastle.Asn1
{
    internal class LazyDLEnumerator
        : IEnumerator<Asn1Encodable>
    {
        private readonly byte[] m_contents;

        private Asn1InputStream m_input;
        private Asn1Object m_current;

        internal LazyDLEnumerator(byte[] contents)
        {
            this.m_contents = contents;

            Reset();
        }

        object System.Collections.IEnumerator.Current
        {
            get { return Current; }
        }

        public Asn1Encodable Current
        {
            get
            {
                if (null == m_current)
                    throw new InvalidOperationException();

                return m_current;
            }
        }

        public virtual void Dispose()
        {
        }

        public bool MoveNext()
        {
            return null != (this.m_current = ReadObject());
        }

        public void Reset()
        {
            this.m_input = new LazyAsn1InputStream(m_contents);
            this.m_current = null;
        }

        private Asn1Object ReadObject()
        {
            try
            {
                return m_input.ReadObject();
            }
            catch (IOException e)
            {
                throw new Asn1ParsingException("malformed ASN.1: " + e.Message, e);
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/LazyDLEnumerator.cs`.

**Classes defined**: LazyDLEnumerator



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 54
- Comment lines: 0
- Blank lines: 12

### Main Components

**Classes** (1):
- `LazyDLEnumerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

