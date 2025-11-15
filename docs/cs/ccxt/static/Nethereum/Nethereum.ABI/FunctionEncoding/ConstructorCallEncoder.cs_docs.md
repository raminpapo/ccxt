# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ConstructorCallEncoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ConstructorCallEncoder.cs`
- **Size**: 1,260 bytes
- **Lines**: 37
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System.Reflection;
using Nethereum.ABI.Model;
using Nethereum.Hex.HexConvertors.Extensions;

namespace Nethereum.ABI.FunctionEncoding
{
    public class ConstructorCallEncoder : ParametersEncoder
    {
        public string EncodeRequest<T>(T constructorInput, string contractByteCode)
        {
            var type = typeof(T);
            var encodedParameters = EncodeParametersFromTypeAttributes(type, constructorInput);
            return EncodeRequest(contractByteCode, encodedParameters.ToHex());
        }

        public string EncodeRequest(string contractByteCode, Parameter[] parameters, params object[] values)
        {
            var parametersEncoded = "";
            if (values != null)
                parametersEncoded = EncodeParameters(parameters, values).ToHex();

            return EncodeRequest(contractByteCode, parametersEncoded);
        }

        public string EncodeRequest(string contractByteCode, string encodedParameters)
        {
            ByteCodeLibraryLinker.EnsureDoesNotContainPlaceholders(contractByteCode);

            var prefix = "0x";

            if (contractByteCode.StartsWith(prefix))
                prefix = "";

            return prefix + contractByteCode + encodedParameters;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/ConstructorCallEncoder.cs`.

**Classes defined**: ConstructorCallEncoder



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 30
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `ConstructorCallEncoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

