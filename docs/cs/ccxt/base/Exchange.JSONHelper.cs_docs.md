# Documentation: cs/ccxt/base/Exchange.JSONHelper.cs

## File Metadata

- **Path**: `cs/ccxt/base/Exchange.JSONHelper.cs`
- **Size**: 2,285 bytes
- **Lines**: 89
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using Newtonsoft.Json;
using Newtonsoft.Json.Linq;

namespace ccxt;

using dict = Dictionary<string, object>;

public partial class Exchange
{

    public static bool isValidJson(string json)
    {
        json = json.Replace("\n", "").Replace("\r", "").Trim();
        if ((json.StartsWith("{") && json.EndsWith("}")) || // For object
            (json.StartsWith("[") && json.EndsWith("]"))) //For array
        {
            return true;
        }
        return false;
    }

    public string stringifyObject(object d2)
    {
        var output = "";

        if (d2 == null)
            return output;

        if (d2.GetType() == typeof(dict))
        {
            var d = (dict)d2;
            if (d == null)
                return output;

            foreach (var key in d.Keys)
            {
                output += key + ", " + d[key] + "\n";
            }
            return output;
        }
        else if (d2.GetType() == typeof(List<object>))
        {
            var d = (List<object>)d2;
            if (d == null)
                return output;

            foreach (var key in d)
            {
                output += key + "\n";
            }
            return output;
        }
        return (string)output;
    }
}

public static class JsonHelper
{
    public static object Deserialize(string json)
    {
        using (var sr = new StringReader(json))
        using (var jr = new JsonTextReader(sr) { DateParseHandling = DateParseHandling.None })
        {
            return ToObject(JToken.ReadFrom(jr)); /// prints '2015-11-23T00:00:00'
            // we need this to avoid wrong dates
            // https://github.com/JamesNK/Newtonsoft.Json/issues/1241
        }
    }

    public static object ToObject(JToken token)
    {
        switch (token.Type)
        {
            case JTokenType.Object:
                return token.Children<JProperty>()
                            .ToDictionary(prop => prop.Name,
                                          prop => ToObject(prop.Value));

            case JTokenType.Array:
                return token.Select(ToObject).ToList();

            case JTokenType.Float:
                return token.ToObject<double>();

            default:
                return ((JValue)token).Value;
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/base/Exchange.JSONHelper.cs`.

**Classes defined**: JsonHelper, Exchange



## Detailed Walkthrough

### Code Structure

- Total lines: 89
- Code lines: 73
- Comment lines: 2
- Blank lines: 14

### Main Components

**Classes** (2):
- `Exchange`
- `JsonHelper`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

