# Documentation: ts/src/static_dependencies/proxies/agent-base/helpers.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/proxies/agent-base/helpers.ts`
- **Size**: 1,271 bytes
- **Lines**: 50
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import * as http from 'http';
import * as https from 'https';
import type { Readable } from 'stream';

export type ThenableRequest = http.ClientRequest & {
	then: Promise<http.IncomingMessage>['then'];
};

export async function toBuffer(stream: Readable): Promise<Buffer> {
	let length = 0;
	const chunks: Buffer[] = [];
	for await (const chunk of stream) {
		length += chunk.length;
		chunks.push(chunk);
	}
	return Buffer.concat(chunks, length);
}

// eslint-disable-next-line @typescript-eslint/no-explicit-any
export async function json(stream: Readable): Promise<any> {
	const buf = await toBuffer(stream);
	const str = buf.toString('utf8');
	try {
		return JSON.parse(str);
	} catch (_err: unknown) {
		const err = _err as Error;
		err.message += ` (input: ${str})`;
		throw err;
	}
}

export function req(
	url: string | URL,
	opts: https.RequestOptions = {}
): ThenableRequest {
	const href = typeof url === 'string' ? url : url.href;
	const req = (href.startsWith('https:') ? https : http).request(
		url,
		opts
	) as ThenableRequest;
	const promise = new Promise<http.IncomingMessage>((resolve, reject) => {
		req
			.once('response', resolve)
			.once('error', reject)
			.end() as ThenableRequest;
	});
	req.then = promise.then.bind(promise);
	return req;
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/proxies/agent-base/helpers.ts`.

**Functions defined**: toBuffer, json, req

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 44
- Comment lines: 1
- Blank lines: 5

### Main Components

**Functions** (3):
- `json()`
- `req()`
- `toBuffer()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `https` (imported)
- `http` (imported)
- `stream` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/proxies/agent-base/helpers.ts
```

