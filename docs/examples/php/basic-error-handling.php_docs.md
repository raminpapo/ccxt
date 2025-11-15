# Documentation: examples/php/basic-error-handling.php

## File Metadata

- **Path**: `examples/php/basic-error-handling.php`
- **Size**: 426 bytes
- **Lines**: 28
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\bittrex ();

$message = null;

try {

    $result = $exchange->fetch_ticker ('NONEXISTENT_SYMBOL');
    var_dump ($result);

} catch (Exception $e) {

    // print it
    echo $e->getMessage() . "\n";

    // save to $message (for whatever needs)
    $message = $e->getMessage();
}

?>

```

## High-Level Overview

This is a PHP file located at `examples/php/basic-error-handling.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 14
- Comment lines: 2
- Blank lines: 12

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
php examples/php/basic-error-handling.php
```

