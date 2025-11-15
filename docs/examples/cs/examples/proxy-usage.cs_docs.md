# Documentation: examples/cs/examples/proxy-usage.cs

## File Metadata

- **Path**: `examples/cs/examples/proxy-usage.cs`
- **Size**: 1,552 bytes
- **Lines**: 44
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using ccxt;
using ccxt.pro;

namespace examples;

partial class Examples
{
// ABOUT CCXT PROXIES, READ MORE AT: https://docs.ccxt.com/#/README?id=proxy
    async public Task proxyUsage_proxyUrl()
    {
        var myEx = new ccxt.kucoin();
        myEx.proxyUrl = "http://5.75.153.75:8090/proxy_url.php?caller=https://ccxt.com&url=";
        Console.WriteLine(await myEx.fetch("https://api.ipify.org/"));
    }

    async public Task proxyUsage_httpProxy()
    {
        var myEx = new ccxt.kucoin();
        myEx.httpProxy = "http://5.75.153.75:8002"; // "httpProxy" or "httpsProxy" (depending on your proxy protocol)
        Console.WriteLine(await myEx.fetch("https://api.ipify.org/"));
    }

    async public Task proxyUsage_socksProxy()
    {
        var myEx = new ccxt.kucoin();
        myEx.socksProxy = "socks5://127.0.0.1:1080"; // from protocols: socks, socks5, socks5h
        Console.WriteLine(await myEx.fetch("https://api.ipify.org/"));
    }

    async public Task proxyUsage_webSockets()
    {
        var myEx = new ccxt.pro.kucoin();
        myEx.httpProxy =
            "http://5.75.153.75:8002"; // even though you are using WebSockets, you might also need to set up proxy for the exchange's REST requests
        myEx.wsProxy =
            "http://5.75.153.75:8002"; // "wsProxy" or "wssProxy" or "wsSocksProxy" (depending on your proxy protocol)
        await myEx.loadMarkets();
        while (true)
        {
            var ticker = await myEx.watchTicker("BTC/USDT");
            Console.WriteLine(ticker);
        }
    }
}
```

## High-Level Overview

This is a C# file located at `examples/cs/examples/proxy-usage.cs`.

**Classes defined**: Examples



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 38
- Comment lines: 1
- Blank lines: 5

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

