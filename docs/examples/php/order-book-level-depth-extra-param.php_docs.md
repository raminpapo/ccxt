# Documentation: examples/php/order-book-level-depth-extra-param.php

## File Metadata

- **Path**: `examples/php/order-book-level-depth-extra-param.php`
- **Size**: 334 bytes
- **Lines**: 16
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

// instantiate the exchange by id
$exchange = '\\ccxt\\kraken';
$exchange = new $exchange ();
$limit = 10; // up to ten order on each side, for example
var_dump ($exchange->fetch_order_book ('BTC/USD', $limit));


?>
```

## High-Level Overview

This is a PHP file located at `examples/php/order-book-level-depth-extra-param.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 9
- Comment lines: 1
- Blank lines: 6

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/order-book-level-depth-extra-param.php
```

