# Documentation: ts/src/base/ws/WsClient.ts

## File Metadata

- **Path**: `ts/src/base/ws/WsClient.ts`
- **Size**: 2,356 bytes
- **Lines**: 80
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// eslint-disable-next-line no-shadow
import WebSocket from 'ws';
import Client from './Client.js';

import {
    sleep,
    isNode,
    milliseconds,
    selfIsDefined,
} from '../../base/functions.js';
import { Future } from './Future.js';

// eslint-disable-next-line no-restricted-globals
const WebSocketPlatform = isNode || !selfIsDefined() ? WebSocket : self.WebSocket;

export default class WsClient extends Client {

    connectionStarted: number | undefined;

    protocols: any;

    options: any;

    startedConnecting: boolean = false;

    createConnection () {
        if (this.verbose) {
            this.log (new Date (), 'connecting to', this.url)
        }
        this.connectionStarted = milliseconds ()
        this.setConnectionTimeout ()
        if (isNode) {
            this.connection = new WebSocketPlatform (this.url, this.protocols, this.options)
        } else {
            this.connection = new WebSocketPlatform (this.url, this.protocols)
        }

        this.connection.onopen = this.onOpen.bind (this)
        this.connection.onmessage = this.onMessage.bind (this)
        this.connection.onerror = this.onError.bind (this)
        this.connection.onclose = this.onClose.bind (this)
        if (isNode) {
            this.connection
                .on ('ping', this.onPing.bind (this))
                .on ('pong', this.onPong.bind (this))
                .on ('upgrade', this.onUpgrade.bind (this))
        }
        // this.connection.terminate () // debugging
        // this.connection.close () // debugging
    }

    connect (backoffDelay = 0) {
        if (!this.startedConnecting) {
            this.startedConnecting = true
            // exponential backoff for consequent ws connections if necessary
            if (backoffDelay) {
                sleep (backoffDelay).then (this.createConnection.bind (this))
            } else {
                this.createConnection ()
            }
        }
        return this.connected
    }

    isOpen () {
        return (this.connection.readyState === WebSocketPlatform.OPEN)
    }

    close () {
        if (this.connection instanceof WebSocketPlatform) {
            if (this.disconnected === undefined) {
                this.disconnected = Future ();
            }
            this.connection.close ();
        }
        return this.disconnected;
    }

}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/base/ws/WsClient.ts`.

**Classes defined**: WsClient

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 61
- Comment lines: 5
- Blank lines: 14

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

**To execute this TypeScript file:**

```bash
ts-node ts/src/base/ws/WsClient.ts
```

