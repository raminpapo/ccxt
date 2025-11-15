# Documentation: examples/js/env-variables.js

## File Metadata

- **Path**: `examples/js/env-variables.js`
- **Size**: 719 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

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

## High-Level Overview

This is a JavaScript file located at `examples/js/env-variables.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 13
- Comment lines: 3
- Blank lines: 11

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

**To execute this JavaScript file:**

```bash
node examples/js/env-variables.js
```

