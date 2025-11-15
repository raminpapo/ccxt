# Documentation: wiki/examples/php/huobi-fetch-balance.md

## File Metadata

- **Path**: `wiki/examples/php/huobi-fetch-balance.md`
- **Size**: 670 bytes
- **Lines**: 32
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Huobi Fetch Balance](./examples/php/)


 ```php
 <?php

include './ccxt.php';

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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/huobi-fetch-balance.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 21
- Comment lines: 1
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

