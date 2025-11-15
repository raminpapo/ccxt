# Documentation: js/src/static_dependencies/proxies/https-proxy-agent/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/proxies/https-proxy-agent/index.d.ts`
- **Size**: 1,989 bytes
- **Lines**: 46
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
export declare type HttpsProxyAgentOptions<T> = ConnectOpts<T> & http.AgentOptions & {
    headers?: OutgoingHttpHeaders | (() => OutgoingHttpHeaders);
};
/**
 * The `HttpsProxyAgent` implements an HTTP Agent subclass that connects to
 * the specified "HTTP(s) proxy server" in order to proxy HTTPS requests.
 *
 * Outgoing HTTP requests are first tunneled through the proxy server using the
 * `CONNECT` HTTP request method to establish a connection to the proxy server,
 * and then the proxy server connects to the destination target and issues the
 * HTTP request from the proxy server.
 *
 * `https:` requests have their socket connection upgraded to TLS once
 * the connection to the proxy server has been established.
 */
export declare class HttpsProxyAgent<Uri extends string> extends Agent {
    static protocols: readonly ["http", "https"];
    readonly proxy: URL;
    proxyHeaders: OutgoingHttpHeaders | (() => OutgoingHttpHeaders);
    connectOpts: net.TcpNetConnectOpts & tls.ConnectionOptions;
    get secureProxy(): boolean;
    constructor(proxy: Uri | URL, opts?: HttpsProxyAgentOptions<Uri>);
    /**
     * Called when the node-core HTTP client library is creating a
     * new HTTP request.
     */
    connect(req: http.ClientRequest, opts: AgentConnectOpts): Promise<net.Socket>;
}
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/proxies/https-proxy-agent/index.d.ts`.

**Classes defined**: HttpsProxyAgent

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 42
- Comment lines: 19
- Blank lines: -15

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
ts-node js/src/static_dependencies/proxies/https-proxy-agent/index.d.ts
```

