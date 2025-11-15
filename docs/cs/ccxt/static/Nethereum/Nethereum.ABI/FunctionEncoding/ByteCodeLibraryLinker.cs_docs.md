# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ByteCodeLibraryLinker.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ByteCodeLibraryLinker.cs`
- **Size**: 1,543 bytes
- **Lines**: 40
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.Hex.HexConvertors.Extensions;
namespace Nethereum.ABI.FunctionEncoding
{
    public class ByteCodeLibraryLinker
    {
        public static readonly string CONTAINS_PLACEHOLDERS_MESSAGE = $"The byte code contains library address placeholders (prefix: '{ByteCodeConstants.LIBRARY_PLACEHOLDER_PREFIX}', suffix: '{ByteCodeConstants.LIBRARY_PLACEHOLDER_SUFFIX}').";

        public static void EnsureDoesNotContainPlaceholders(string byteCode)
        {
            if (ContainsPlaceholders(byteCode))
            {
                throw new System.Exception(CONTAINS_PLACEHOLDERS_MESSAGE);
            }
        }

        public static bool ContainsPlaceholders(string byteCode)
        {
            if(string.IsNullOrEmpty(byteCode)) return false;
            //for efficiency only check for prefix
            return byteCode.Contains(ByteCodeConstants.LIBRARY_PLACEHOLDER_PREFIX);
        }

        private static string CreatePlaceholder(string key)
        {
            return ByteCodeConstants.LIBRARY_PLACEHOLDER_PREFIX + key + ByteCodeConstants.LIBRARY_PLACEHOLDER_SUFFIX;
        }

        public string LinkByteCode(string byteCode, params ByteCodeLibrary[] byteCodeLibraries)
        {
            foreach (var byteCodeLibrary in byteCodeLibraries)
            {
                var placeholder = CreatePlaceholder(byteCodeLibrary.PlaceholderKey);
                byteCode = byteCode.Replace(placeholder, byteCodeLibrary.Address.RemoveHexPrefix());
            }
            return byteCode;
        }


    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ByteCodeLibraryLinker.cs`.

**Classes defined**: ByteCodeLibraryLinker



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 33
- Comment lines: 1
- Blank lines: 6

### Main Components

**Classes** (1):
- `ByteCodeLibraryLinker`

**Constants** (1):
- `CONTAINS_PLACEHOLDERS_MESSAGE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

