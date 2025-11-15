# Documentation: js/src/pro/test/custom/server.d.ts

## File Metadata

- **Path**: `js/src/pro/test/custom/server.d.ts`
- **Size**: 228 bytes
- **Lines**: 8
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
declare class WebSocketServer {
    constructor(config?: {});
    onConnection(ws: any, request: any): void;
    error(ws: any): void;
    onUpgrade(request: any, socket: any, head: any): void;
}
export default WebSocketServer;

```

## High-Level Overview

This is a TypeScript file located at `js/src/pro/test/custom/server.d.ts`.

**Classes defined**: WebSocketServer



## Detailed Walkthrough

### Code Structure

- Total lines: 8
- Code lines: 7
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `WebSocketServer`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/custom/server.d.ts
```

