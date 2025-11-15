# Documentation: js/src/base/ws/Client.d.ts

## File Metadata

- **Path**: `js/src/base/ws/Client.d.ts`
- **Size**: 1,734 bytes
- **Lines**: 55
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Future } from './Future.js';
import { Dictionary, Str } from '../types.js';
export default class Client {
    connected: Promise<any>;
    disconnected: ReturnType<typeof Future>;
    futures: Dictionary<any>;
    rejections: Dictionary<any>;
    keepAlive: number;
    connection: any;
    connectionTimeout: any;
    verbose: boolean;
    connectionTimer: any;
    lastPong: any;
    maxPingPongMisses: any;
    pingInterval: any;
    connectionEstablished: any;
    gunzip: any;
    error: any;
    inflate: any;
    url: string;
    isConnected: any;
    onConnectedCallback: any;
    onMessageCallback: any;
    onErrorCallback: any;
    onCloseCallback: any;
    ping: any;
    subscriptions: Dictionary<any>;
    throttle: any;
    decompressBinary: boolean;
    constructor(url: string, onMessageCallback: Function | undefined, onErrorCallback: Function | undefined, onCloseCallback: Function | undefined, onConnectedCallback: Function | undefined, config?: {});
    reusableFuture(messageHash: string): any;
    future(messageHash: string): any;
    resolve(result: any, messageHash: Str): any;
    reject(result: any, messageHash?: Str): any;
    log(...args: any[]): void;
    connect(backoffDelay?: number): void;
    isOpen(): boolean;
    reset(error: any): void;
    onConnectionTimeout(): void;
    setConnectionTimeout(): void;
    clearConnectionTimeout(): void;
    setPingInterval(): void;
    clearPingInterval(): void;
    onPingInterval(): void;
    onOpen(): void;
    onPing(): void;
    onPong(): void;
    onError(error: any): void;
    onClose(event: any): void;
    onUpgrade(message: any): void;
    send(message: any): Promise<any>;
    close(): void;
    onMessage(messageEvent: any): void;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/ws/Client.d.ts`.

**Classes defined**: Client

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 54
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `Client`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./Future.js` (imported)
- `../types.js` (imported)
- `./Future.js` (referenced)
- `../types.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/ws/Client.d.ts
```

