# Documentation: js/src/test/Exchange/test.proxies.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.proxies.js`
- **Size**: 4,193 bytes
- **Lines**: 81
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testSharedMethods from './base/test.sharedMethods.js';
async function testProxies(exchange, skippedProperties) {
    await testProxyUrl(exchange, skippedProperties);
    await testHttpProxy(exchange, skippedProperties);
    // 'httpsProxy', 'socksProxy'
    await testProxyForExceptions(exchange, skippedProperties);
}
async function testProxyUrl(exchange, skippedProperties) {
    const method = 'proxyUrl';
    const proxyServerIp = '5.75.153.75';
    const [proxyUrl, httpProxy, httpsProxy, socksProxy] = testSharedMethods.removeProxyOptions(exchange, skippedProperties);
    exchange.proxyUrl = 'http://' + proxyServerIp + ':8090/proxy_url.php?caller=https://ccxt.com&url=';
    const encodedColon = '%3A';
    const encodedSlash = '%2F';
    const ipCheckUrl = 'https' + encodedColon + encodedSlash + encodedSlash + 'api.ipify.org';
    const response = await exchange.fetch(ipCheckUrl);
    assert(response === proxyServerIp, exchange.id + ' ' + method + ' test failed. Returned response is ' + response + ' while it should be "' + proxyServerIp + '"');
    // reset the instance property
    testSharedMethods.setProxyOptions(exchange, skippedProperties, proxyUrl, httpProxy, httpsProxy, socksProxy);
    return true;
}
async function testHttpProxy(exchange, skippedProperties) {
    const method = 'httpProxy';
    const proxyServerIp = '5.75.153.75';
    const [proxyUrl, httpProxy, httpsProxy, socksProxy] = testSharedMethods.removeProxyOptions(exchange, skippedProperties);
    exchange.httpProxy = 'http://' + proxyServerIp + ':8911';
    const ipCheckUrl = 'https://api.ipify.org/';
    const response = await exchange.fetch(ipCheckUrl);
    assert(response === proxyServerIp, exchange.id + ' ' + method + ' test failed. Returned response is ' + response + ' while it should be "' + proxyServerIp + '"');
    // reset the instance property
    testSharedMethods.setProxyOptions(exchange, skippedProperties, proxyUrl, httpProxy, httpsProxy, socksProxy);
}
// with the below method we test out all variations of possible proxy options, so at least 2 of them should be set together, and such cases must throw exception
async function testProxyForExceptions(exchange, skippedProperties) {
    const method = 'testProxyForExceptions';
    const [proxyUrl, httpProxy, httpsProxy, socksProxy] = testSharedMethods.removeProxyOptions(exchange, skippedProperties);
    const possibleOptionsArray = [
        'proxyUrl',
        'proxyUrlCallback',
        'proxy_url',
        'proxy_url_callback',
        'httpProxy',
        'httpProxyCallback',
        'http_proxy',
        'http_proxy_callback',
        'httpsProxy',
        'httpsProxyCallback',
        'https_proxy',
        'https_proxy_callback',
        'socksProxy',
        'socksProxyCallback',
        'socks_proxy',
        'socks_proxy_callback'
    ];
    for (let i = 0; i < possibleOptionsArray.length; i++) {
        for (let j = 0; j < possibleOptionsArray.length; j++) {
            if (j !== i) {
                const proxyFirst = possibleOptionsArray[i];
                const proxySecond = possibleOptionsArray[j];
                exchange.setProperty(exchange, proxyFirst, '0.0.0.0'); // actual value does not matter
                exchange.setProperty(exchange, proxySecond, '0.0.0.0'); // actual value does not matter
                let exceptionCaught = false;
                try {
                    await exchange.fetch('http://example.com'); // url does not matter, it will not be called
                }
                catch (e) {
                    exceptionCaught = true;
                }
                assert(exceptionCaught, exchange.id + ' ' + method + ' test failed. No exception was thrown, while ' + proxyFirst + ' and ' + proxySecond + ' were set together');
                // reset to undefined
                exchange.setProperty(exchange, proxyFirst, undefined);
                exchange.setProperty(exchange, proxySecond, undefined);
            }
        }
    }
    // reset the instance property
    testSharedMethods.setProxyOptions(exchange, skippedProperties, proxyUrl, httpProxy, httpsProxy, socksProxy);
}
export default testProxies;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.proxies.js`.

**Functions defined**: testHttpProxy, testProxyForExceptions, testProxies, testProxyUrl

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 74
- Comment lines: 6
- Blank lines: 1

### Main Components

**Functions** (4):
- `testHttpProxy()`
- `testProxies()`
- `testProxyForExceptions()`
- `testProxyUrl()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `http://example.com` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.proxies.js
```

