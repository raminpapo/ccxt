# Documentation: wiki/examples/php/error-handling-message.md

## File Metadata

- **Path**: `wiki/examples/php/error-handling-message.md`
- **Size**: 1,137 bytes
- **Lines**: 56
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Error Handling Message](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\bittrex(array(
    'apiKey' => 'foo',
    'secret' => 'bar',
));

$message = null;

try {

    $result = $exchange->fetch_balance ();
    var_dump ($result);

// these catch-clauses are showing the proper way of handling the errors

} catch (\ccxt\AuthenticationError $e) {

    // handle authentication error here

} catch (\ccxt\NetworkError $e) {

    // your code to handle the network code and retries here

} catch (\ccxt\ExchangeError $e) {

    // your code to handle an exchange error

} catch (Exception $e) {

    // This is an example of how NOT TO DO error handling
    // One should not rely on the message string contained in the exception
    // If you want to access it, that might indicate a design error in your code.
    // See: https://github.com/ccxt/ccxt/issues/3053

    $message = $e->getMessage();

    if (preg_match ('/[a-z]+\s+(\{.+\})$/iu', $e->getMessage(), $matches)) {
        $message = $matches[1];
    }

    echo print_r ($message, true) . "\n";

}

?>
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/error-handling-message.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 25
- Comment lines: 8
- Blank lines: 23

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

