# Documentation: wiki/examples/php/basic-error-handling.md

## File Metadata

- **Path**: `wiki/examples/php/basic-error-handling.md`
- **Size**: 431 bytes
- **Lines**: 31
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Basic Error Handling](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\bittrex ();

$message = null;

try {

    $result = $exchange->fetch_ticker ('NONEXISTENT_SYMBOL');
    var_dump ($result);

} catch (Exception $e) {

    // print it
    echo $e->getMessage() . "\n";

    // save to $message (for whatever needs)
    $message = $e->getMessage();
}

?>
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/basic-error-handling.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 16
- Comment lines: 2
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

