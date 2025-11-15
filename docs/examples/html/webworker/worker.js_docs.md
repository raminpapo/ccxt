# Documentation: examples/html/webworker/worker.js

## File Metadata

- **Path**: `examples/html/webworker/worker.js`
- **Size**: 1,313 bytes
- **Lines**: 43
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
self.importScripts('https://unpkg.com/ccxt@1.79.2/dist/ccxt.browser.js');

console.log("Loaded ccxt version:", self.ccxt.version);

var exchangeInstance = undefined;

// handler of received messages
self.onmessage = async function handler(msg) {
  await handleMessageFromMain(msg)
}

// get messages from the main script
async function handleMessageFromMain(msg) {
  console.log(msg.data);
  var [exchange, symbol, interval] = msg.data;
  console.log('Worker received:', symbol,exchange, interval)
  interval = parseInt(interval)
  await processTicker(symbol, exchange)  
  // schedule process ticker execution
  setInterval (async () => {
    await processTicker(symbol, exchange)  
  }, interval)
}

async function processTicker(symbol, exchangeId) {
  if (exchangeInstance === undefined) {
    exchangeInstance = new ccxt[exchangeId]
  }
  var result = await fetchTicker(symbol)
  var symbol = result['symbol']
  var last = result['last']
  var timestamp = result['timestamp']
  var baseVolume = result['baseVolume']
  var ourTimestamp = Date.now()
  // send the data back to the main script
  postMessage([symbol, last, baseVolume, timestamp, ourTimestamp]);
}

async function fetchTicker(symbol){
  // use ccxt to fetch ticker info
  var result = await exchangeInstance.fetchTicker(symbol)
  return result;
}
```

## High-Level Overview

This is a JavaScript file located at `examples/html/webworker/worker.js`.

**Functions defined**: processTicker, fetchTicker, handler, handleMessageFromMain



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 32
- Comment lines: 5
- Blank lines: 6

### Main Components

**Functions** (4):
- `fetchTicker()`
- `handleMessageFromMain()`
- `handler()`
- `processTicker()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `https://unpkg.com/ccxt@1.79.2/dist/ccxt.browser.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/html/webworker/worker.js
```

