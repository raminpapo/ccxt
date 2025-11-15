# Documentation: wiki/examples/ts/custom-proxy-agent-for-js.md

## File Metadata

- **Path**: `wiki/examples/ts/custom-proxy-agent-for-js.md`
- **Size**: 529 bytes
- **Lines**: 18
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Custom Proxy Agent For Js](./examples/ts/)


 ```javascript
 // @ts-nocheck
// to set custom "proxy-agent" for ccxt
import ccxt from 'ccxt';
import HttpProxyAgent from 'http-proxy-agent';
import HttpsProxyAgent from 'https-proxy-agent';
const proxy = 'http://1.2.3.4:5678';
const httpAgent = new HttpProxyAgent (proxy); 
const httpsAgent = new HttpsProxyAgent (proxy);
// then pass it through constructor
const kraken = new ccxt.kraken ({ agent: httpAgent /* or httpsAgent */ });
// or set it later
kraken.agent = agent;
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/ts/custom-proxy-agent-for-js.md`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 11
- Comment lines: 4
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `http-proxy-agent` (imported)
- `ccxt` (imported)
- `https-proxy-agent` (imported)



## Testing & Execution

**To execute this Markdown file:**

