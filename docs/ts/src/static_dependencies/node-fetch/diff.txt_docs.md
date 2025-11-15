# Documentation: ts/src/static_dependencies/node-fetch/diff.txt

## File Metadata

- **Path**: `ts/src/static_dependencies/node-fetch/diff.txt`
- **Size**: 1,582 bytes
- **Lines**: 44
- **Type**: Plain Text
- **Extension**: .txt


## Original Source Code

```
diff ts/src/static_dependencies/node-fetch/body.js node_modules/node-fetch/src/body.js
12,13c12,13
< // import Blob from 'fetch-blob';
< // import {FormData, formDataToBlob} from 'formdata-polyfill/esm.min.js';
---
> import Blob from 'fetch-blob';
> import {FormData, formDataToBlob} from 'formdata-polyfill/esm.min.js';
55,56c55,56
< 		} /* else if (body instanceof FormData) {
< 			Body is FormData
---
> 		} else if (body instanceof FormData) {
> 			// Body is FormData
59,60c59
< 		} */
< 		else {
---
> 		} else {
Only in ts/src/static_dependencies/node-fetch: diff.txt
Common subdirectories: ts/src/static_dependencies/node-fetch/errors and node_modules/node-fetch/src/errors
Only in ts/src/static_dependencies/node-fetch: index.d.ts
diff ts/src/static_dependencies/node-fetch/index.js node_modules/node-fetch/src/index.js
24c24
< // import {FormData} from 'formdata-polyfill/esm.min.js';
---
> import {FormData} from 'formdata-polyfill/esm.min.js';
27c27
< /* import {
---
> import {
34c34
< } from 'fetch-blob/from.js';*/
---
> } from 'fetch-blob/from.js';
36,39c36,37
< // export {FormData, Headers, Request, Response, FetchError, AbortError, isRedirect};
< // export {Blob, File, fileFromSync, fileFrom, blobFromSync, blobFrom};
< 
< export {Headers, Request, Response, FetchError, AbortError, isRedirect};
---
> export {FormData, Headers, Request, Response, FetchError, AbortError, isRedirect};
> export {Blob, File, fileFromSync, fileFrom, blobFromSync, blobFrom};
Common subdirectories: ts/src/static_dependencies/node-fetch/utils and node_modules/node-fetch/src/utils

```

## High-Level Overview

This is a Plain Text file located at `ts/src/static_dependencies/node-fetch/diff.txt`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 43
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `fetch-blob/from.js` (imported)
- `fetch-blob` (imported)
- `formdata-polyfill/esm.min.js` (imported)
- `fetch-blob/from.js` (referenced)
- `formdata-polyfill/esm.min.js` (referenced)



## Testing & Execution

**To execute this Plain Text file:**

