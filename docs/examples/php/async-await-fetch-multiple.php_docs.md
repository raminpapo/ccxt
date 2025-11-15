# Documentation: examples/php/async-await-fetch-multiple.php

## File Metadata

- **Path**: `examples/php/async-await-fetch-multiple.php`
- **Size**: 750 bytes
- **Lines**: 23
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
// Instead of yield generators, now users can use modern Async/Await syntax
include dirname(dirname(dirname(__FILE__))) . '/ccxt.php';
date_default_timezone_set('UTC');

use function React\Async\async;
use function React\Async\await;
use function React\Promise\all;

$exchange = new ccxt\async\binance([]);
await($exchange->load_markets());
$symbols = array('BTC/USDT', 'ETH/USDT', 'DOGE/USDT');


echo "########### Combined await ###########\n";
$promises = [];
foreach ($symbols as $symbol) {
    $promises[] = $exchange->fetch_ticker($symbol);
}
$tickers = await(all($promises));

echo "{$tickers[0]['symbol']} {$tickers[0]['close']}  |  {$tickers[1]['symbol']} {$tickers[1]['close']}  |  {$tickers[21]['symbol']} {$tickers[2]['close']}\n";

```

## High-Level Overview

This is a PHP file located at `examples/php/async-await-fetch-multiple.php`.

**Functions defined**: React



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 16
- Comment lines: 1
- Blank lines: 6

### Main Components

**Functions** (1):
- `React()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/async-await-fetch-multiple.php
```

