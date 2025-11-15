# Documentation: js/src/static_dependencies/starknet/utils/url.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/url.d.ts`
- **Size**: 1,036 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * Loosely validate a URL `string`.
 *
 * @param {string} s - The URL to check for
 * @return {boolean} `true` if url is valid, `false` otherwise
 * @example
 * ```typescript
 * const s = "https://starknetjs.com/docs";
 * const result = isUrl(s);
 * // result == true
 */
export declare function isUrl(s?: string): boolean;
/**
 * Builds a URL using the provided base URL, default path, and optional URL or path.
 *
 * @param {string} baseUrl - The base URL of the URL being built.
 * @param {string} defaultPath - The default path to use if no URL or path is provided.
 * @param {string} [urlOrPath] - The optional URL or path to append to the base URL.
 * @return {string} The built URL.
 * @example
 * ```typescript
 * const baseUrl = "https://starknetjs.com";
 * const defaultPath = "/";
 * const urlOrPath = "/docs";
 * const result = buildUrl(baseUrl, defaultPath, urlOrPath);
 *
 * result = "https://starknetjs.com/docs"
 */
export declare function buildUrl(baseUrl: string, defaultPath: string, urlOrPath?: string): string;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/url.d.ts`.

**Functions defined**: isUrl, buildUrl

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 29
- Comment lines: 27
- Blank lines: -26

### Main Components

**Functions** (2):
- `buildUrl()`
- `isUrl()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `https://starknetjs.com` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/url.d.ts
```

