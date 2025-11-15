# Documentation: js/src/static_dependencies/proxies/https-proxy-agent/parse-proxy-response.js

## File Metadata

- **Path**: `js/src/static_dependencies/proxies/https-proxy-agent/parse-proxy-response.js`
- **Size**: 3,285 bytes
- **Lines**: 90
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export function parseProxyResponse(socket) {
    return new Promise((resolve, reject) => {
        // we need to buffer any HTTP traffic that happens with the proxy before we get
        // the CONNECT response, so that if the response is anything other than an "200"
        // response code, then we can re-play the "data" events on the socket once the
        // HTTP parser is hooked up...
        let buffersLength = 0;
        const buffers = [];
        function read() {
            const b = socket.read();
            if (b)
                ondata(b);
            else
                socket.once('readable', read);
        }
        function cleanup() {
            socket.removeListener('end', onend);
            socket.removeListener('error', onerror);
            socket.removeListener('close', onclose);
            socket.removeListener('readable', read);
        }
        function onclose(err) {
            // debug('onclose had error %o', err);
        }
        function onend() {
            // debug('onend');
        }
        function onerror(err) {
            cleanup();
            // debug('onerror %o', err);
            reject(err);
        }
        function ondata(b) {
            buffers.push(b);
            buffersLength += b.length;
            const buffered = Buffer.concat(buffers, buffersLength);
            const endOfHeaders = buffered.indexOf('\r\n\r\n');
            if (endOfHeaders === -1) {
                // keep buffering
                // debug('have not received end of HTTP headers yet...');
                read();
                return;
            }
            const headerParts = buffered.toString('ascii').split('\r\n');
            const firstLine = headerParts.shift();
            if (!firstLine) {
                throw new Error('No header received');
            }
            const firstLineParts = firstLine.split(' ');
            const statusCode = +firstLineParts[1];
            const statusText = firstLineParts.slice(2).join(' ');
            const headers = {};
            for (const header of headerParts) {
                if (!header)
                    continue;
                const firstColon = header.indexOf(':');
                if (firstColon === -1) {
                    throw new Error(`Invalid header: "${header}"`);
                }
                const key = header.slice(0, firstColon).toLowerCase();
                const value = header.slice(firstColon + 1).trimStart();
                const current = headers[key];
                if (typeof current === 'string') {
                    headers[key] = [current, value];
                }
                else if (Array.isArray(current)) {
                    current.push(value);
                }
                else {
                    headers[key] = value;
                }
            }
            // debug('got proxy server response: %o', firstLine);
            cleanup();
            resolve({
                connect: {
                    statusCode,
                    statusText,
                    headers,
                },
                buffered,
            });
        }
        socket.on('error', onerror);
        socket.on('close', onclose);
        socket.on('end', onend);
        read();
    });
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/proxies/https-proxy-agent/parse-proxy-response.js`.

**Functions defined**: parseProxyResponse, onerror, onclose, read, onend, cleanup, ondata



## Detailed Walkthrough

### Code Structure

- Total lines: 90
- Code lines: 79
- Comment lines: 10
- Blank lines: 1

### Main Components

**Functions** (7):
- `cleanup()`
- `onclose()`
- `ondata()`
- `onend()`
- `onerror()`
- `parseProxyResponse()`
- `read()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/proxies/https-proxy-agent/parse-proxy-response.js
```

