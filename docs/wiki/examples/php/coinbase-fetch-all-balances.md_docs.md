# Documentation: wiki/examples/php/coinbase-fetch-all-balances.md

## File Metadata

- **Path**: `wiki/examples/php/coinbase-fetch-all-balances.md`
- **Size**: 1,123 bytes
- **Lines**: 45
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Fetch All Balances](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\coinbase(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET',
    // 'verbose' => true, // uncomment for debugging
));

$exchange->load_markets();

// $exchange->verbose = true; // uncomment for debugging

$result = array();
$params = array();
$loop = true;
do {
    $balance = $exchange->fetch_balance($params);
    $pagination = $exchange->safe_value($balance['info'], 'pagination');
    if ($pagination === null) {
        $loop = false;
    } else {
        $next_starting_after = $exchange->safe_string ($pagination, 'next_starting_after');
        if ($next_starting_after !== null) {
            $params['starting_after'] = $next_starting_after;
        } else {
            $loop = false;
        }
    }
    echo $exchange->iso8601($exchange->milliseconds()) . "\n";
    $result = $exchange->deep_extend($result, $balance);
} while ($loop);

echo "======================================================================\n";
var_dump($result);

?> 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/coinbase-fetch-all-balances.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 33
- Comment lines: 2
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

