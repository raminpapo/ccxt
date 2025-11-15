# Documentation: examples/cs/examples/compare-two-exchanges-capabilities.cs

## File Metadata

- **Path**: `examples/cs/examples/compare-two-exchanges-capabilities.cs`
- **Size**: 2,462 bytes
- **Lines**: 61
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;
namespace examples;
partial class Examples
{
    async public Task compareTwoExchangesCapabilities()
    {
        var prefix = "-";
        var exchange1 = new ccxt.okx();
        var exchange2 = new ccxt.htx();
        var keys1 = exchange1.has.Keys.ToList();
        var keys2 = exchange2.has.Keys.ToList();


        Console.WriteLine("### checking missing functionalities from exchange-1:" + exchange1.id);
        for (var i = 0; i < keys1.Count; i++)
        {
            var key = keys2[i];
            if (((bool)exchange1.has[key]))
            {
                if (!keys2.Contains(key))
                {
                    var msg = prefix + key + "does not exist in" + exchange1.id + "as opposed to" + exchange2.id;
                    Console.WriteLine(msg);
                }
                else if (exchange1.has[key] != exchange2.has[key])
                {
                    var msg = prefix + key + "> " + exchange1.id + ":" + exchange1.has[key] + "," + exchange2.id + ":" + exchange2.has[key];
                    Console.WriteLine(msg);
                }
                {
                    var msg = prefix + key + "> " + exchange1.id + ":" + exchange1.has[key].ToString() + " +" + exchange2.id + ":" + exchange2.has[key].ToString();
                    Console.WriteLine(msg);
                }
            }
        }
        // check missing from exchange-2
        Console.WriteLine("### checking missing functionalities from exchange-2:", exchange2.id);
        for (var i = 0; i < keys2.Count; i++)
        {
            var key = keys1[i];
            if (((bool)exchange2.has[key]))
            {
                if (!keys1.Contains(key))
                {
                    var msg = prefix + key + "does not exist in" + exchange2.id + "as opposed to" + exchange1.id;
                    Console.WriteLine(msg);
                }
                else if (exchange2.has[key] != exchange1.has[key])
                {
                    var msg = prefix + key + "> " + exchange2.id + ":" + exchange2.has[key] + "," + exchange1.id + ":" + exchange1.has[key];
                    Console.WriteLine(msg);
                }
                {
                    var msg = prefix + key + "> " + exchange2.id + ":" + exchange2.has[key].ToString() + " +" + exchange1.id + ":" + exchange1.has[key].ToString();
                    Console.WriteLine(msg);
                }
            }
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/compare-two-exchanges-capabilities.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 58
- Comment lines: 1
- Blank lines: 2

### Main Components

**Classes** (1):
- `Examples`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

