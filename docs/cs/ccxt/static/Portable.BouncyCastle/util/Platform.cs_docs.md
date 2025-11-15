# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/Platform.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/Platform.cs`
- **Size**: 1,808 bytes
- **Lines**: 60
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Globalization;

namespace Org.BouncyCastle.Utilities
{
    internal abstract class Platform
    {
        private static readonly CompareInfo InvariantCompareInfo = CultureInfo.InvariantCulture.CompareInfo;

        internal static bool EqualsIgnoreCase(string a, string b)
        {
            return string.Equals(a, b, StringComparison.OrdinalIgnoreCase);
        }

        internal static string GetEnvironmentVariable(string variable)
        {
            try
            {
                return Environment.GetEnvironmentVariable(variable);
            }
            catch (System.Security.SecurityException)
            {
                // We don't have the required permission to read this environment variable,
                // which is fine, just act as if it's not set
                return null;
            }
        }

        internal static void Dispose(IDisposable d)
        {
            d.Dispose();
        }

        internal static int IndexOf(string source, string value)
        {
            return InvariantCompareInfo.IndexOf(source, value, CompareOptions.Ordinal);
        }

        internal static int LastIndexOf(string source, string value)
        {
            return InvariantCompareInfo.LastIndexOf(source, value, CompareOptions.Ordinal);
        }

        internal static bool StartsWith(string source, string prefix)
        {
            return InvariantCompareInfo.IsPrefix(source, prefix, CompareOptions.Ordinal);
        }

        internal static bool EndsWith(string source, string suffix)
        {
            return InvariantCompareInfo.IsSuffix(source, suffix, CompareOptions.Ordinal);
        }

        internal static string GetTypeName(object obj)
        {
            return obj.GetType().FullName;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/Platform.cs`.

**Classes defined**: Platform



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 48
- Comment lines: 2
- Blank lines: 10

### Main Components

**Classes** (1):
- `Platform`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

