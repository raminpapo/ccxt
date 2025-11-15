# Documentation: examples/php/kraken-query-ledgers.php

## File Metadata

- **Path**: `examples/php/kraken-query-ledgers.php`
- **Size**: 604 bytes
- **Lines**: 31
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';
// include 'Console/Table.php';

date_default_timezone_set('UTC');

// instantiate the exchange by id

$exchange = '\\ccxt\\kraken';
$exchange = new $exchange(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET_KEY',
));

// get ledgers
$ledgers = $exchange->privatePostLedgers ();

// get ledger ids
$ids = array_keys ($ledgers['result']['ledger']);

// get ledger entries for ledger id
$ledger_entries = $exchange->privatePostQueryLedgers(array(
    'id' =>  $ids[0],
));

var_dump ($ledger_entries);

?>
```

## High-Level Overview

This is a PHP file located at `examples/php/kraken-query-ledgers.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 16
- Comment lines: 5
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `Console/Table.php` (referenced)
- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/kraken-query-ledgers.php
```

