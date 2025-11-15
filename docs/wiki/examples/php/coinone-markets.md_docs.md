# Documentation: wiki/examples/php/coinone-markets.md

## File Metadata

- **Path**: `wiki/examples/php/coinone-markets.md`
- **Size**: 321 bytes
- **Lines**: 20
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinone Markets](./examples/php/)


 ```php
 <?php

include './ccxt.php';

$exchange = new \ccxt\coinone(array(
    // 'verbose' => true, // uncomment for verbose output
));

$markets = $exchange->load_markets();

var_dump($markets);
echo "\n" . $exchange->name . " supports " . count($markets) . " pairs\n";

?>
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/coinone-markets.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 11
- Comment lines: 1
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

