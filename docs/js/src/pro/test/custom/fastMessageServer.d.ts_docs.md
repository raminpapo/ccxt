# Documentation: js/src/pro/test/custom/fastMessageServer.d.ts

## File Metadata

- **Path**: `js/src/pro/test/custom/fastMessageServer.d.ts`
- **Size**: 202 bytes
- **Lines**: 7
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
declare class WebSocketServer {
    constructor(config?: {});
    onConnection(ws: any, request: any): void;
    onUpgrade(request: any, socket: any, head: any): void;
}
export default WebSocketServer;

```

## High-Level Overview

This is a TypeScript file located at `js/src/pro/test/custom/fastMessageServer.d.ts`.

**Classes defined**: WebSocketServer



## Detailed Walkthrough

### Code Structure

- Total lines: 7
- Code lines: 6
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
npm test js/src/pro/test/custom/fastMessageServer.d.ts
```

