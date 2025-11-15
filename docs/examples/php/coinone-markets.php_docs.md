# Documentation: examples/php/coinone-markets.php

## File Metadata

- **Path**: `examples/php/coinone-markets.php`
- **Size**: 321 bytes
- **Lines**: 17
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

$exchange = new \ccxt\coinone(array(
    // 'verbose' => true, // uncomment for verbose output
));

$markets = $exchange->load_markets();

var_dump($markets);
echo "\n" . $exchange->name . " supports " . count($markets) . " pairs\n";

?>

```

## High-Level Overview

This is a PHP file located at `examples/php/coinone-markets.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 9
- Comment lines: 1
- Blank lines: 7

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
php examples/php/coinone-markets.php
```

