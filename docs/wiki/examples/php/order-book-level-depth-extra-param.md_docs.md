# Documentation: wiki/examples/php/order-book-level-depth-extra-param.md

## File Metadata

- **Path**: `wiki/examples/php/order-book-level-depth-extra-param.md`
- **Size**: 353 bytes
- **Lines**: 19
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Order Book Level Depth Extra Param](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

// instantiate the exchange by id
$exchange = '\\ccxt\\kraken';
$exchange = new $exchange ();
$limit = 10; // up to ten order on each side, for example
var_dump ($exchange->fetch_order_book ('BTC/USD', $limit));


?> 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/order-book-level-depth-extra-param.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 11
- Comment lines: 1
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

