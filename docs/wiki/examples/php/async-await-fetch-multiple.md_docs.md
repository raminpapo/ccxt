# Documentation: wiki/examples/php/async-await-fetch-multiple.md

## File Metadata

- **Path**: `wiki/examples/php/async-await-fetch-multiple.md`
- **Size**: 814 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Await Fetch Multiple](./examples/php/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/async-await-fetch-multiple.md`.

**Functions defined**: React



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 19
- Comment lines: 1
- Blank lines: 8

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

**To execute this Markdown file:**

