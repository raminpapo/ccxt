# Documentation: wiki/examples/php/react-eventloop-with-rate-limiting.md

## File Metadata

- **Path**: `wiki/examples/php/react-eventloop-with-rate-limiting.md`
- **Size**: 1,063 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [React Eventloop With Rate Limiting](./examples/php/)


 ```php
 <?php

require dirname(__FILE__).'/../vendor/autoload.php';
include dirname(__FILE__) ."/../vendor/ccxt/ccxt/ccxt.php";

date_default_timezone_set('UTC');

use TomWright\Database\ExtendedPDO\ExtendedPDO as ExtendedPDO;
use TomWright\Database\QueryBuilder\SqlQueryBuilder as SqlQueryBuilder;

$loop = React\EventLoop\Factory::create ();

// instantiate the exchange by id
$exchange = '\\ccxt\\poloniex';
$exchange = new $exchange ();

$tick_function = function () use ($exchange, $loop, &$tick_function) {
    global $exchange, $loop;
    $order_book = $exchange->fetch_order_book ($symbol);
    echo "----------------------------------------------------------------\n";
    echo date ('c') . "\n";
    echo count ($order_book['bids']) . " bids and " . count ($order_book['asks']) . " asks\n";
    echo sprintf ("bid: %.8f ask: %.8f", $order_book['bids'][0][0], $order_book['asks'][0][0]) . "\n";

    $loop->futureTick ($tick_function);
};

$loop->futureTick ($tick_function);
$loop->run (); 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/react-eventloop-with-rate-limiting.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 23
- Comment lines: 1
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/../vendor/ccxt/ccxt/ccxt.php` (referenced)
- `/../vendor/autoload.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

