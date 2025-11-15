# Documentation: wiki/examples/js/env-variables.md

## File Metadata

- **Path**: `wiki/examples/js/env-variables.md`
- **Size**: 776 bytes
- **Lines**: 32
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Env Variables](./examples/js/)


 ```javascript
 

// ----------------------------------------------------------------------------

import ccxt from '../../js/ccxt.js';
import ololog from 'ololog'

// ----------------------------------------------------------------------------

const log = ololog.configure.handleNodeErrors (), asTable = require("as-table").configure({ delimiter: " | " });

// ----------------------------------------------------------------------------

(async () => {

    const exchange = new ccxt.coinbase ({
        verbose: process.argv.includes ('--verbose'),
        timeout: 60000,
        apiKey: process.env.KEY,
        secret: process.env.SECRET
    });

    const balance = await exchange.fetchBalance ()
    log.green (balance)

})()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/env-variables.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 16
- Comment lines: 3
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `ololog` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

