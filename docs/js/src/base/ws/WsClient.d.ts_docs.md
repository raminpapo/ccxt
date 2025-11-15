# Documentation: js/src/base/ws/WsClient.d.ts

## File Metadata

- **Path**: `js/src/base/ws/WsClient.d.ts`
- **Size**: 351 bytes
- **Lines**: 12
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import Client from './Client.js';
export default class WsClient extends Client {
    connectionStarted: number | undefined;
    protocols: any;
    options: any;
    startedConnecting: boolean;
    createConnection(): void;
    connect(backoffDelay?: number): Promise<any>;
    isOpen(): boolean;
    close(): import("./Future.js").FutureInterface;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/ws/WsClient.d.ts`.

**Classes defined**: WsClient

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 11
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./Client.js` (imported)
- `./Future.js` (referenced)
- `./Client.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/ws/WsClient.d.ts
```

