# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Hash/MemberValueFactory.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Hash/MemberValueFactory.cs`
- **Size**: 6,401 bytes
- **Lines**: 161
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using Nethereum.ABI;
using Nethereum.ABI.FunctionEncoding;
using Nethereum.ABI.Model;
using System.Collections;
using System.Collections.Generic;
using System.Linq;

namespace StarkSharp.StarkSharp.Base.StarkSharp.Hash
{
    public class MemberValueFactory
    {
        private static readonly ParametersEncoder _parametersEncoder = new ParametersEncoder();
        public static MemberValue[] CreateFromMessage<T>(T message)
        {
            var parameters = _parametersEncoder.GetParameterAttributeValues(typeof(T), message).OrderBy(x => x.ParameterAttribute.Order);
            var typeValues = new List<MemberValue>();
            foreach (var parameterAttributeValue in parameters)
            {
                if (parameterAttributeValue.ParameterAttribute.Parameter.ABIType is TupleType tupleType)
                {
                    
                    typeValues.Add(CreateFromTuple(parameterAttributeValue.ParameterAttribute.Parameter, parameterAttributeValue.Value));
                }
                else if (parameterAttributeValue.ParameterAttribute.Parameter.ABIType is ArrayType arrayType)
                {

                    if (arrayType.ElementType is TupleType tupleTypeElement)
                    {
                        var input = parameterAttributeValue.Value as IList;
                        if (input == null)
                        {
                            typeValues.Add(new MemberValue
                            {
                                TypeName = parameterAttributeValue.ParameterAttribute.StructTypeName,
                                Value = new List<MemberValue>()
                            }); 
                        }
                        else
                        {
                            var arrayMemberValue = new List<MemberValue[]>();
                            foreach (var itemValue in input)
                            {
                                arrayMemberValue.Add(CreateFromTuple(tupleTypeElement, itemValue));
                            }

                            typeValues.Add(new MemberValue
                            {
                                TypeName = parameterAttributeValue.ParameterAttribute.StructTypeName,
                                Value = arrayMemberValue
                            });
                        }
                    }
                    else
                    {
                        typeValues.Add(new MemberValue
                        {
                            TypeName = parameterAttributeValue.ParameterAttribute.Type,
                            Value = parameterAttributeValue.Value
                        });
                    }
                }
                else
                {
                    typeValues.Add(new MemberValue
                    {
                        TypeName = parameterAttributeValue.ParameterAttribute.Type,
                        Value = parameterAttributeValue.Value
                    });
                }
            }

            return typeValues.ToArray();

        }

        public static MemberValue[] CreateFromTuple(TupleType tupleType, object value)
        {
            var structValue = new List<MemberValue>();

            var input = value as object[];
            if(input == null)
            {
                input = _parametersEncoder.GetTupleComponentValuesFromTypeAttributes(value.GetType(), value);
            }

            if (input == null)
            {
               return structValue.ToArray();
            }

            for (int i = 0; i < input.Length; i++)
            {
                var structInnerValue = new MemberValue();
                var component = tupleType.Components[i];
                if (component.ABIType is TupleType tupleTypeComponent)
                {
                    structInnerValue.TypeName = component.StructTypeName;
                    structInnerValue.Value = CreateFromTuple(tupleTypeComponent, input[i]);
                    structValue.Add(structInnerValue);
                } 
                else if (component.ABIType is ArrayType arrayType)
                { 
                
                    if (arrayType.ElementType is TupleType tupleTypeElement)
                    {
                        var innerInput = input[i] as object[];

                        if (innerInput == null)
                        {
                            innerInput = _parametersEncoder.GetTupleComponentValuesFromTypeAttributes(input[i].GetType(), input[i]);
                        }

                        if (innerInput == null)
                        {
                            structInnerValue.TypeName = component.StructTypeName;
                            structInnerValue.Value = new List<MemberValue>();
                        }
                        else
                        {
                            var arrayMemberValue = new List<MemberValue[]>();
                            foreach (var itemValue in innerInput)
                            {
                                arrayMemberValue.Add(CreateFromTuple(tupleTypeElement, itemValue));
                            }

                            structInnerValue.TypeName = component.StructTypeName;
                            structInnerValue.Value = arrayMemberValue;
                            
                        }
                    }
                    else
                    {
                        structInnerValue.TypeName = component.Type;
                        structInnerValue.Value = input[i];
                        structValue.Add(structInnerValue);
                    }

                }
                else
                {
                    structInnerValue.TypeName = component.Type;
                    structInnerValue.Value = input[i];
                    structValue.Add(structInnerValue);
                }

            }
            return structValue.ToArray();
        }


        public static MemberValue CreateFromTuple(Parameter structParameter, object value)
        {
            var memberValue = new MemberValue();
            var tupleType = structParameter.ABIType as TupleType;

            memberValue.TypeName = structParameter.StructTypeName;
            memberValue.Value = CreateFromTuple(tupleType, value);
            return memberValue;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Base/StarkSharp.Hash/MemberValueFactory.cs`.

**Classes defined**: MemberValueFactory



## Detailed Walkthrough

### Code Structure

- Total lines: 161
- Code lines: 141
- Comment lines: 0
- Blank lines: 20

### Main Components

**Classes** (1):
- `MemberValueFactory`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

