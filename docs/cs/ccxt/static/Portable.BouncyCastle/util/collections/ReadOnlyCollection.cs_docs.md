# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/collections/ReadOnlyCollection.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/collections/ReadOnlyCollection.cs`
- **Size**: 1,465 bytes
- **Lines**: 45
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;

namespace Org.BouncyCastle.Utilities.Collections
{
    internal abstract class ReadOnlyCollection<T>
        : ICollection<T>
    {
        System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator()
        {
            return GetEnumerator();
        }

        public bool IsReadOnly => true;

        public void Add(T item) => throw new NotSupportedException();
        public void Clear() => throw new NotSupportedException();
        public bool Remove(T item) => throw new NotSupportedException();

        public abstract bool Contains(T item);
        public abstract int Count { get; }
        public abstract void CopyTo(T[] array, int arrayIndex);
        public abstract IEnumerator<T> GetEnumerator();
    }

    internal class ReadOnlyCollectionProxy<T>
        : ReadOnlyCollection<T>
    {
        private readonly ICollection<T> m_target;

        internal ReadOnlyCollectionProxy(ICollection<T> target)
        {
            if (target == null)
                throw new ArgumentNullException(nameof(target));

            m_target = target;
        }

        public override bool Contains(T item) => m_target.Contains(item);
        public override int Count => m_target.Count;
        public override void CopyTo(T[] array, int arrayIndex) => m_target.CopyTo(array, arrayIndex);
        public override IEnumerator<T> GetEnumerator() => m_target.GetEnumerator();
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/collections/ReadOnlyCollection.cs`.

**Classes defined**: ReadOnlyCollection, ReadOnlyCollectionProxy



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 36
- Comment lines: 0
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

