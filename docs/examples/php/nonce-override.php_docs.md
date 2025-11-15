# Documentation: examples/php/nonce-override.php

## File Metadata

- **Path**: `examples/php/nonce-override.php`
- **Size**: 727 bytes
- **Lines**: 32
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

class MillisecondsNonceExchange extends \ccxt\yobit {
    public function nonce() {
        return $this->milliseconds();
    }
}

$exchange = new MillisecondsNonceExchange(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET',
));

try {
    $symbol = 'ETH/BTC';
    $result = $exchange->fetch_balance($symbol);
    var_dump ($result);
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

This is a PHP file located at `examples/php/nonce-override.php`.

**Classes defined**: MillisecondsNonceExchange

**Functions defined**: nonce



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 25
- Comment lines: 0
- Blank lines: 7

### Main Components

**Functions** (1):
- `nonce()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/nonce-override.php
```

