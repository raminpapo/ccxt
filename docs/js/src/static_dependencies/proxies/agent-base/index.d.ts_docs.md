# Documentation: js/src/static_dependencies/proxies/agent-base/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/proxies/agent-base/index.d.ts`
- **Size**: 1,243 bytes
- **Lines**: 34
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/// <reference types="node" />
/// <reference types="node" />
/// <reference types="node" />
/// <reference types="node" />
import * as net from 'net';
import * as tls from 'tls';
import * as http from 'http';
import { Duplex } from 'stream';
export * from './helpers.js';
interface HttpConnectOpts extends net.TcpNetConnectOpts {
    secureEndpoint: false;
    protocol?: string;
}
interface HttpsConnectOpts extends tls.ConnectionOptions {
    secureEndpoint: true;
    protocol?: string;
    port: number;
}
export declare type AgentConnectOpts = HttpConnectOpts | HttpsConnectOpts;
declare const INTERNAL: unique symbol;
export declare abstract class Agent extends http.Agent {
    private [INTERNAL];
    options: Partial<net.TcpNetConnectOpts & tls.ConnectionOptions>;
    keepAlive: boolean;
    constructor(opts?: http.AgentOptions);
    abstract connect(req: http.ClientRequest, options: AgentConnectOpts): Promise<Duplex | http.Agent> | Duplex | http.Agent;
    createSocket(req: http.ClientRequest, options: AgentConnectOpts, cb: (err: Error | null, s?: Duplex) => void): void;
    createConnection(): Duplex;
    get defaultPort(): number;
    set defaultPort(v: number);
    get protocol(): string;
    set protocol(v: string);
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/proxies/agent-base/index.d.ts`.

**Classes defined**: Agent

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 29
- Comment lines: 4
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `net` (imported)
- `http` (imported)
- `stream` (imported)
- `./helpers.js` (imported)
- `tls` (imported)
- `./helpers.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/proxies/agent-base/index.d.ts
```

