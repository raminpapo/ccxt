# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/FormattingExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/FormattingExtensions.cs`
- **Size**: 537 bytes
- **Lines**: 18
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Globalization;

namespace Nethereum.Util
{
    public static class FormattingExtensions
    {
        /// <summary>
        /// Converts formattable value to string in a culture-independent way.
        /// </summary>
        public static string ToStringInvariant<T>(this T formattable) where T : IFormattable
        {
            if (formattable == null) throw new ArgumentNullException(nameof(formattable));

            return formattable.ToString(null, CultureInfo.InvariantCulture);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/FormattingExtensions.cs`.

**Classes defined**: FormattingExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 13
- Comment lines: 3
- Blank lines: 2

### Main Components

**Classes** (1):
- `FormattingExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

