# Documentation: examples/ts/proxy-usage.ts

## File Metadata

- **Path**: `examples/ts/proxy-usage.ts`
- **Size**: 1,934 bytes
- **Lines**: 50
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

// 1) ABOUT CCXT PROXIES, READ MORE AT: https://docs.ccxt.com/#/README?id=proxy
// 2) in python, uncomment the below:
// if sys.platform == 'win32':
//     asyncio.set_event_loop_policy(asyncio.WindowsSelectorEventLoopPolicy())

async function example_proxyUrl () {
    const myEx = new ccxt.kucoin ();
    myEx.proxyUrl = 'http://188.245.226.105:8090/proxy_url.php?caller=https://ccxt.com&url=';
    console.log (await myEx.fetch ('https://api.ipify.org/'));
}

async function example_httpProxy () {
    const myEx = new ccxt.kucoin ();
    myEx.httpProxy = 'http://188.245.226.105:8911'; // "httpProxy" or "httpsProxy" (depending on your proxy protocol)
    console.log (await myEx.fetch ('https://api.ipify.org/'));
}

async function example_socksProxy () {
    const myEx = new ccxt.kucoin ();
    myEx.socksProxy = 'socks5://127.0.0.1:1080'; // from protocols: socks, socks5, socks5h
    console.log (await myEx.fetch ('https://api.ipify.org/'));
}

async function example_webSockets () {
    const myEx = new ccxt.pro.kucoin ();
    myEx.httpProxy = 'http://188.245.226.105:8911'; // even though you are using WebSockets, you might also need to set up proxy for the exchange's REST requests
    myEx.wsProxy = 'http://188.245.226.105:8911'; // "wsProxy" or "wssProxy" or "wsSocksProxy" (depending on your proxy protocol)
    await myEx.loadMarkets ();
    //
    // To ensure your WS proxy works, uncomment below code and watch the log
    //
    // myEx.verbose = true;
    // await myEx.loadHttpProxyAgent ();
    // await myEx.watch ('ws://188.245.226.105:9876/', 'myip'); // in the incoming logs, confirm that you see the proxy IP in "hello" message
    //
    console.log (await myEx.watchTicker ('BTC/USDT'));
    await myEx.close ();
}


// await example_proxyUrl ();
await example_httpProxy ();
// await example_socksProxy ();
// await example_webSockets ();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/proxy-usage.ts`.

**Functions defined**: example_webSockets, example_httpProxy, example_socksProxy, example_proxyUrl

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 25
- Comment lines: 15
- Blank lines: 10

### Main Components

**Functions** (4):
- `example_httpProxy()`
- `example_proxyUrl()`
- `example_socksProxy()`
- `example_webSockets()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node examples/ts/proxy-usage.ts
```

