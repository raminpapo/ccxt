# Documentation: js/src/base/ws/WsClient.js

## File Metadata

- **Path**: `js/src/base/ws/WsClient.js`
- **Size**: 2,310 bytes
- **Lines**: 64
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// eslint-disable-next-line no-shadow
import WebSocket from 'ws';
import Client from './Client.js';
import { sleep, isNode, milliseconds, selfIsDefined, } from '../../base/functions.js';
import { Future } from './Future.js';
// eslint-disable-next-line no-restricted-globals
const WebSocketPlatform = isNode || !selfIsDefined() ? WebSocket : self.WebSocket;
export default class WsClient extends Client {
    constructor() {
        super(...arguments);
        this.startedConnecting = false;
    }
    createConnection() {
        if (this.verbose) {
            this.log(new Date(), 'connecting to', this.url);
        }
        this.connectionStarted = milliseconds();
        this.setConnectionTimeout();
        if (isNode) {
            this.connection = new WebSocketPlatform(this.url, this.protocols, this.options);
        }
        else {
            this.connection = new WebSocketPlatform(this.url, this.protocols);
        }
        this.connection.onopen = this.onOpen.bind(this);
        this.connection.onmessage = this.onMessage.bind(this);
        this.connection.onerror = this.onError.bind(this);
        this.connection.onclose = this.onClose.bind(this);
        if (isNode) {
            this.connection
                .on('ping', this.onPing.bind(this))
                .on('pong', this.onPong.bind(this))
                .on('upgrade', this.onUpgrade.bind(this));
        }
        // this.connection.terminate () // debugging
        // this.connection.close () // debugging
    }
    connect(backoffDelay = 0) {
        if (!this.startedConnecting) {
            this.startedConnecting = true;
            // exponential backoff for consequent ws connections if necessary
            if (backoffDelay) {
                sleep(backoffDelay).then(this.createConnection.bind(this));
            }
            else {
                this.createConnection();
            }
        }
        return this.connected;
    }
    isOpen() {
        return (this.connection.readyState === WebSocketPlatform.OPEN);
    }
    close() {
        if (this.connection instanceof WebSocketPlatform) {
            if (this.disconnected === undefined) {
                this.disconnected = Future();
            }
            this.connection.close();
        }
        return this.disconnected;
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/ws/WsClient.js`.

**Classes defined**: WsClient

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 58
- Comment lines: 5
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../base/functions.js` (imported)
- `./Future.js` (imported)
- `./Client.js` (imported)
- `ws` (imported)
- `../../base/functions.js` (referenced)
- `./Future.js` (referenced)
- `./Client.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/ws/WsClient.js
```

