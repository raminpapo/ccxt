# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/collections/ReadOnlyList.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/collections/ReadOnlyList.cs`
- **Size**: 1,970 bytes
- **Lines**: 60
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;

namespace Org.BouncyCastle.Utilities.Collections
{
    internal abstract class ReadOnlyList<T>
        : IList<T>
    {
        public T this[int index]
        {
            get { return Lookup(index); }
            set { throw new NotSupportedException(); }
        }

        System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator()
        {
            return GetEnumerator();
        }

        public bool IsReadOnly => true;

        public void Add(T item) => throw new NotSupportedException();
        public void Clear() => throw new NotSupportedException();
        public void Insert(int index, T item) => throw new NotSupportedException();
        public bool Remove(T item) => throw new NotSupportedException();
        public void RemoveAt(int index) => throw new NotSupportedException();


        public abstract bool Contains(T item);
        public abstract void CopyTo(T[] array, int arrayIndex);
        public abstract int Count { get; }
        public abstract IEnumerator<T> GetEnumerator();
        public abstract int IndexOf(T item);

        protected abstract T Lookup(int index);
    }

    internal class ReadOnlyListProxy<T>
        : ReadOnlyList<T>
    {
        private readonly IList<T> m_target;

        internal ReadOnlyListProxy(IList<T> target)
        {
            if (target == null)
                throw new ArgumentNullException(nameof(target));

            m_target = target;
        }

        public override int Count => m_target.Count;
        public override bool Contains(T item) => m_target.Contains(item);
        public override void CopyTo(T[] array, int arrayIndex) => m_target.CopyTo(array, arrayIndex);
        public override IEnumerator<T> GetEnumerator() => m_target.GetEnumerator();
        public override int IndexOf(T item) => m_target.IndexOf(item);

        protected override T Lookup(int index) => m_target[index];
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/collections/ReadOnlyList.cs`.

**Classes defined**: ReadOnlyListProxy, ReadOnlyList



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 47
- Comment lines: 0
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

