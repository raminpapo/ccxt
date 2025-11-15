# Documentation: ts/src/pro/test/custom/fastMessageServer.ts

## File Metadata

- **Path**: `ts/src/pro/test/custom/fastMessageServer.ts`
- **Size**: 3,963 bytes
- **Lines**: 117
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// @ts-nocheck

import WebSocket from 'ws'
import http from 'http'
import { extend } from '../../../base/functions'

// ----------------------------------------------------------------------------
// a sandbox ws server for testing and debugging

class WebSocketServer {

    constructor (config = {}) {

        const defaults = {
            "terminateTimeout": undefined, // terminate the connection immediately or later
            "closeTimeout": undefined, // close after a while
            "closeCode": 1000, // default closing code 1000 = ok
            "handshakeDelay": undefined, // delay the handshake to simulate connection timeout
            "port": 8080,
        }

        // merge to this
        const entries = Object.entries (extend (defaults, config))
        for (let i = 0; i < entries.length; i++) {
            const [ property, value ] = entries[i]
            this[property] = value
        }

        this.server = http.createServer ()
        thiss = new WebSocket.Server ({ "noServer": true })
        thiss.on ('connection', this.onConnection.bind (this))
        this.server.on ('upgrade', this.onUpgrade.bind (this))

        console.log (new Date (), 'listening port', this.port)
        this.server.listen (this.port)
    }

    onConnection (ws, request) {

        console.log (new Date (), 'onConnection')

        // terminate any incoming connection
        // immediately after it has been successfully established
        if (Number.isInteger (this.terminateTimeout)) {
            if (this.terminateTimeout) {
                setTimeout (() => { ws.terminate () }, this.terminateTimeout)
            } else {
                ws.terminate ()
            }
        }

        // close the connection after a certain amount of time
        if (Number.isInteger (this.closeTimeout)) {
            if (this.closeTimeout) {
                setTimeout (() => {
                    console.log (new Date (), 'Closing with code', this.closeCode, typeof this)
                    // ws.terminate ()
                    ws.close (this.closeCode)
                }, this.closeTimeout)
            } else {
                ws.close (this.closeCode)
            }
        }

        // ws.send ('something')
        let i = 0
        const blaster = setInterval (() => {
            console.log ('sending ' + i)
            ws.send (i++)
        }, 1)
        // sleep in the php code to see the lag

        // other stuff that might be useful
        ws.on ('message', (message) => {
            console.log (new Date (), 'onMessage', message)
            // ws.send (message) // echo back
        })
        ws.on ('ping', (message) => {
            console.log (new Date (), 'onPing', message.toString ())
            // ws.pong () // ws sends pong automatically
        })
        ws.on ('pong', (message) => {
            console.log (new Date (), 'onPong', message)
        })
        ws.on ('close', (code) => {
            console.log (new Date (), 'onClose', code)
            clearInterval (blaster)
        })
        // ws.ping ()
    }

    onUpgrade (request, socket, head) {
        console.log (new Date (), 'onUpgrade')
        if (Number.isInteger (this.handshakeDelay)) {
            console.log (new Date (), 'handshake delay', this.handshakeDelay)
            setTimeout (() => {
                thiss.handleUpgrade (request, socket, head, ((ws) => {
                    thiss.emit ('connection', ws, request)
                }))
            }, this.handshakeDelay)
        } else {
            thiss.handleUpgrade (request, socket, head, ((ws) => {
                thiss.emit ('connection', ws, request)
            }))
        }
    }
}

export default WebSocketServer

// ----------------------------------------------------------------------------
// if launched in console instead of being required as a module

if (require.main === module) {
    (async () => { const wss = new WebSocketServer () }) ()
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/custom/fastMessageServer.ts`.

**Classes defined**: WebSocketServer

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 117
- Code lines: 82
- Comment lines: 16
- Blank lines: 19

### Main Components

**Classes** (1):
- `WebSocketServer`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `http` (imported)
- `../../../base/functions` (imported)
- `ws` (imported)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/custom/fastMessageServer.ts
```

