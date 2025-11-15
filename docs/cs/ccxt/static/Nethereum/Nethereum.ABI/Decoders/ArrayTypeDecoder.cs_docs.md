# Documentation: cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ArrayTypeDecoder.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ArrayTypeDecoder.cs`
- **Size**: 5,975 bytes
- **Lines**: 161
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Reflection;
using Nethereum.ABI.FunctionEncoding;
using Nethereum.ABI.FunctionEncoding.Attributes;

namespace Nethereum.ABI.Decoders
{
    public class ArrayTypeDecoder : TypeDecoder
    {
        private readonly AttributesToABIExtractor _attributesToABIExtractor;

        public ArrayTypeDecoder(ABIType elementType, int size)
        {
            Size = size;
            ElementType = elementType;
            _attributesToABIExtractor = new AttributesToABIExtractor();
        }

        public int Size { get; protected set; }

        protected ABIType ElementType { get; set; }

        public override object Decode(byte[] encoded, Type type)
        {
            return Decode(encoded, type, Size);
        }

        protected object Decode(byte[] encoded, Type type, int size)
        {
            if (ElementType.IsDynamic())
                return DecodeDynamicElementType(encoded, type, size);
            return DecodeStaticElementType(encoded, type, size);
        }

        public override Type GetDefaultDecodingType()
        {
            return typeof(List<>).MakeGenericType(new[] { ElementType.GetDefaultDecodingType() });
        }

        public override bool IsSupportedType(Type type)
        {
            return GetIListElementType(type) != null;
        }

        protected virtual object DecodeDynamicElementType(byte[] encoded, Type type, int size)
        {
            if (size * 32 > encoded.Length) throw new Exception($@"Insufficient data length to decode Array. Data: {encoded.Length}, Size: {size}");

            var decodedListOutput = (IList) Activator.CreateInstance(type);



            if (decodedListOutput == null)
                throw new Exception("Only types that implement IList<T> are supported to decode Array Types");

            var elementType = GetIListElementType(type);

            if (elementType == null)
                throw new Exception("Only types that implement IList<T> are supported to decode Array Types");

            var intDecoder = new IntTypeDecoder();
            var dataIndexes = new List<int>();

            var currentIndex = 0;

            while (currentIndex < size)
            {
                dataIndexes.Add(intDecoder.DecodeInt(encoded.Skip(currentIndex * 32).Take(32).ToArray()));
                currentIndex++;
            }

            currentIndex = 0;

            while (currentIndex < size)
            {
                var currentDataIndex = dataIndexes[currentIndex];
                var nextDataIndex = encoded.Length;
                if (currentIndex + 1 < dataIndexes.Count) nextDataIndex = dataIndexes[currentIndex + 1];
                var encodedElement =
                    encoded.Skip(currentDataIndex).Take(nextDataIndex - currentDataIndex).ToArray();

                DecodeAndAddElement(elementType, decodedListOutput, encodedElement);

                currentIndex++;
            }

            return decodedListOutput;
        }

        private void DecodeAndAddElement(Type elementType, IList decodedList, byte[] encodedElement)
        {
            if (ElementType is TupleType tupleTypeElement)
            {
                if (elementType == typeof(List<ParameterOutput>))
                {
                    decodedList.Add(ElementType.Decode(encodedElement, elementType));
                }
                else
                {
                    InitTupleElementComponents(elementType, tupleTypeElement);
                    decodedList.Add(new ParameterDecoder().DecodeAttributes(encodedElement, elementType));
                }
            }
            else
            {
                decodedList.Add(ElementType.Decode(encodedElement, elementType));
            }
        }

        protected void InitTupleElementComponents(Type elementType, TupleType tupleTypeElement)
        {
            if (tupleTypeElement.Components == null)
                _attributesToABIExtractor.InitTupleComponentsFromTypeAttributes(elementType,
                    tupleTypeElement);
        }

        protected virtual object DecodeStaticElementType(byte[] encoded, Type type, int size)
        {
            if (size * 32 > encoded.Length) throw new Exception($@"Insufficient data length to decode Array. Data: {encoded.Length}, Size: {size}");

            var decodedListOutput = (IList) Activator.CreateInstance(type);

            if (decodedListOutput == null)
                throw new Exception("Only types that implement IList<T> are supported to decoded Array Types");

            var elementType = GetIListElementType(type);

            if (elementType == null)
                throw new Exception("Only types that implement IList<T> are supported to decoded Array Types");

            var currentIndex = 0;

            while (currentIndex < size)
            {
                var encodedElement = encoded.Skip(currentIndex * ElementType.FixedSize).Take(ElementType.FixedSize).ToArray();
                DecodeAndAddElement(elementType, decodedListOutput, encodedElement);
                currentIndex++;
            }

            return decodedListOutput;
        }

        public static Type GetIListElementType(Type listType)
        {
#if DOTNET35
            var enumType = listType.GetTypeInfo().ImplementedInterfaces()
            .Where(i => i.GetTypeInfo().IsGenericType && (i.GenericTypeArguments().Length == 1))
            .FirstOrDefault(i => i.GetGenericTypeDefinition() == typeof(IEnumerable<>));
            return enumType?.GenericTypeArguments()[0];
#else
            var enumType = listType.GetTypeInfo().ImplementedInterfaces
                .Where(i => i.GetTypeInfo().IsGenericType && i.GenericTypeArguments.Length == 1)
                .FirstOrDefault(i => i.GetGenericTypeDefinition() == typeof(IEnumerable<>));
            return enumType?.GenericTypeArguments[0];
#endif
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.ABI/Decoders/ArrayTypeDecoder.cs`.

**Classes defined**: ArrayTypeDecoder



## Detailed Walkthrough

### Code Structure

- Total lines: 161
- Code lines: 124
- Comment lines: 3
- Blank lines: 34

### Main Components

**Classes** (1):
- `ArrayTypeDecoder`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

