# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/JsonParameterObjectConvertor.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/JsonParameterObjectConvertor.cs`
- **Size**: 2,661 bytes
- **Lines**: 79
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI.Model;
using Nethereum.Hex.HexConvertors.Extensions;
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Numerics;
using System.Text;

namespace Nethereum.ABI.FunctionEncoding
{
    public static class JsonParameterObjectConvertor
    {
        public static object[] ConvertToFunctionInputParameterValues(this JToken jObject, FunctionABI function)
        {
            return ConvertToFunctionInputParameterValues(jObject, function.InputParameters);
        }

        public static object[] ConvertToFunctionInputParameterValues(this JToken jObject, Parameter[] parameters)
        {
            var output = new List<object>();
            var parametersInOrder = parameters.OrderBy(x => x.Order);
            foreach (var parameter in parametersInOrder)
            {
                var abiType = parameter.ABIType;
                var jToken = jObject[parameter.GetParameterNameUsingDefaultIfNotSet()];

                AddJTokenValueInputParameters(output, abiType, jToken);
            }

            return output.ToArray();
        }

        private static void AddJTokenValueInputParameters(List<object> inputParameters, ABIType abiType, JToken jToken)
        {
            var tupleAbi = abiType as TupleType;
            if (tupleAbi != null)
            {
                var tupleValue = jToken;
                inputParameters.Add(ConvertToFunctionInputParameterValues(tupleValue, tupleAbi.Components));
            }

            var arrayAbi = abiType as ArrayType;
            if (arrayAbi != null)
            {
                var array = (JArray)jToken;
                var elementType = arrayAbi.ElementType;
                var arrayOutput = new List<object>();
                foreach (var element in array)
                {
                    AddJTokenValueInputParameters(arrayOutput, elementType, element);
                }
                inputParameters.Add(arrayOutput);
            }

            if (abiType is Bytes32Type || abiType is BytesType)
            {
                var bytes = jToken.ToObject<string>().HexToByteArray();
                inputParameters.Add(bytes);
            }

            if (abiType is StringType || abiType is AddressType)
            {
                inputParameters.Add(jToken.ToObject<string>());
            }

            if (abiType is IntType)
            {
                inputParameters.Add(BigInteger.Parse(jToken.ToObject<string>()));
            }

            if (abiType is BoolType)
            {
                inputParameters.Add(jToken.ToObject<bool>());
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/FunctionEncoding/JsonParameterObjectConvertor.cs`.

**Classes defined**: JsonParameterObjectConvertor



## Detailed Walkthrough

### Code Structure

- Total lines: 79
- Code lines: 68
- Comment lines: 0
- Blank lines: 11

### Main Components

**Classes** (1):
- `JsonParameterObjectConvertor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

