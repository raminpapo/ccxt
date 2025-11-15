# Documentation: wiki/examples/php/load-all-at-once.md

## File Metadata

- **Path**: `wiki/examples/php/load-all-at-once.md`
- **Size**: 1,497 bytes
- **Lines**: 45
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Load All At Once](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchanges = \ccxt\Exchange::$exchanges;

foreach ($exchanges as $exchange) {
    $id = "\\ccxt\\".$exchange;
    $exchange = new $id();
    echo "--------------------------------------------\n";
    echo $exchange->id . "\n";

    try {
        $markets = $exchange->load_markets ();
        echo count (array_values ($exchange->markets)) . " markets: " .
            implode (', ', array_slice ($exchange->symbols, 0, 5)) . "...\n";
    } catch (\ccxt\RequestTimeout $e) {
        echo '[Timeout Error] ' . $e->getMessage() . ' (ignoring)' . "\n";
    } catch (\ccxt\DDoSProtection $e) {
        echo '[DDoS Protection Error] ' . $e->getMessage() . ' (ignoring)' . "\n";
    } catch (\ccxt\AuthenticationError $e) {
        echo '[Authentication Error] ' . $e->getMessage() . ' (ignoring)' . "\n";
    } catch (\ccxt\ExchangeNotAvailable $e) {
        echo '[Exchange Not Available] ' . $e->getMessage() . ' (ignoring)' . "\n";
    } catch (\ccxt\NotSupported $e) {
        echo '[Not Supported] ' . $e->getMessage() . ' (ignoring)' . "\n";
    } catch (\ccxt\NetworkError $e) {
        echo '[Network Error] ' . $e->getMessage() . ' (ignoring)' . "\n";
    } catch (\ccxt\ExchangeError $e) {
        echo '[Exchange Error] ' . $e->getMessage() . ' (ignoring)' . "\n";
    } catch (Exception $e) {
        echo '[Error] ' . $e->getMessage() . "\n";
    }
    echo "\n";
}


?> 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/load-all-at-once.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 36
- Comment lines: 0
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

