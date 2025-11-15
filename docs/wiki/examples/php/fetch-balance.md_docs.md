# Documentation: wiki/examples/php/fetch-balance.md

## File Metadata

- **Path**: `wiki/examples/php/fetch-balance.md`
- **Size**: 656 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Balance](./examples/php/)


 ```php
 <?php

include dirname(dirname(dirname(__FILE__))) . '/ccxt.php';
date_default_timezone_set('UTC');

$exchange = new \ccxt\okx(array(
    // 'verbose' => true, // for debugging
    // 'timeout' => 30000,
    "apiKey" => "YOUR_API_KEY",
    "secret" => "YOUR_API_SECRET",
));

try {
	// about balance, read docs at : https://github.com/ccxt/ccxt/wiki/Manual#balance-structure
    $result = $exchange->fetch_balance ();
    print_r ($result);

} catch (\ccxt\NetworkError $e) {
    echo '[Network Error] ' . $e->getMessage() . "\n";
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/fetch-balance.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 18
- Comment lines: 3
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

