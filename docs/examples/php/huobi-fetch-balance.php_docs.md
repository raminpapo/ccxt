# Documentation: examples/php/huobi-fetch-balance.php

## File Metadata

- **Path**: `examples/php/huobi-fetch-balance.php`
- **Size**: 666 bytes
- **Lines**: 29
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\huobipro(array(
    'apiKey' => 'YOUR_API_KEY', // ←------------ replace with your keys
    'secret' => 'YOUR_SECRET',
    // 'verbose' => true, // uncomment if debug output is needed
));

try {

    $balance = $exchange->fetch_balance ();
    var_dump ($balance);

} catch (\ccxt\NetworkError $e) {
    echo '[Network Error] ' . $e->getMessage() . "\n";
} catch (\ccxt\ExchangeError $e) {
    echo '[Exchange Error] ' . $e->getMessage() . "\n";
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}

?>

```

## High-Level Overview

This is a PHP file located at `examples/php/huobi-fetch-balance.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 19
- Comment lines: 1
- Blank lines: 9

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
php examples/php/huobi-fetch-balance.php
```

