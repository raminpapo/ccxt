# Documentation: wiki/examples/php/nonce-override.md

## File Metadata

- **Path**: `wiki/examples/php/nonce-override.md`
- **Size**: 726 bytes
- **Lines**: 35
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Nonce Override](./examples/php/)


 ```php
 <?php

include './ccxt.php';

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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/nonce-override.md`.

**Classes defined**: MillisecondsNonceExchange

**Functions defined**: nonce



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 27
- Comment lines: 0
- Blank lines: 8

### Main Components

**Functions** (1):
- `nonce()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

