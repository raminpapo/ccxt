# Documentation: wiki/examples/js/hybridCJSExample.md

## File Metadata

- **Path**: `wiki/examples/js/hybridCJSExample.md`
- **Size**: 549 bytes
- **Lines**: 24
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Hybridcjsexample](./examples/js/)


 ```javascript
 
const ccxt = require('ccxt');

console.log('--------------------------------------------')
console.log('Yey importing ccxt as a cjs module!!!!!')
console.log('Version:', ccxt.version)
console.log('--------------------------------------------')

const exchange = new ccxt.huobi ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
    'options': {
        'defaultType': 'swap',
    },
})
;(async () => {
const result = await exchange.fetchBalance();
console.log(result)
}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/hybridCJSExample.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 19
- Comment lines: 0
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

