# Documentation: js/src/static_dependencies/proxies/http-proxy-agent/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/proxies/http-proxy-agent/index.d.ts`
- **Size**: 1,644 bytes
- **Lines**: 41
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/// <reference types="node" />
/// <reference types="node" />
/// <reference types="node" />
import * as net from 'net';
import * as tls from 'tls';
import * as http from 'http';
import type { OutgoingHttpHeaders } from 'http';
import { Agent, AgentConnectOpts } from './../agent-base/index.js';
declare type Protocol<T> = T extends `${infer Protocol}:${infer _}` ? Protocol : never;
declare type ConnectOptsMap = {
    http: Omit<net.TcpNetConnectOpts, 'host' | 'port'>;
    https: Omit<tls.ConnectionOptions, 'host' | 'port'>;
};
declare type ConnectOpts<T> = {
    [P in keyof ConnectOptsMap]: Protocol<T> extends P ? ConnectOptsMap[P] : never;
}[keyof ConnectOptsMap];
export declare type HttpProxyAgentOptions<T> = ConnectOpts<T> & http.AgentOptions & {
    headers?: OutgoingHttpHeaders | (() => OutgoingHttpHeaders);
};
interface HttpProxyAgentClientRequest extends http.ClientRequest {
    outputData?: {
        data: string;
    }[];
    _header?: string | null;
    _implicitHeader(): void;
}
/**
 * The `HttpProxyAgent` implements an HTTP Agent subclass that connects
 * to the specified "HTTP proxy server" in order to proxy HTTP requests.
 */
export declare class HttpProxyAgent<Uri extends string> extends Agent {
    static protocols: readonly ["http", "https"];
    readonly proxy: URL;
    proxyHeaders: OutgoingHttpHeaders | (() => OutgoingHttpHeaders);
    connectOpts: net.TcpNetConnectOpts & tls.ConnectionOptions;
    get secureProxy(): boolean;
    constructor(proxy: Uri | URL, opts?: HttpProxyAgentOptions<Uri>);
    connect(req: HttpProxyAgentClientRequest, opts: AgentConnectOpts): Promise<net.Socket>;
}
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/proxies/http-proxy-agent/index.d.ts`.

**Classes defined**: HttpProxyAgent

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 37
- Comment lines: 7
- Blank lines: -3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `net` (imported)
- `http` (imported)
- `./../agent-base/index.js` (imported)
- `tls` (imported)
- `./../agent-base/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/proxies/http-proxy-agent/index.d.ts
```

