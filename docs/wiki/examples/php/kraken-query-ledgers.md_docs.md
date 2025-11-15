# Documentation: wiki/examples/php/kraken-query-ledgers.md

## File Metadata

- **Path**: `wiki/examples/php/kraken-query-ledgers.md`
- **Size**: 609 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Kraken Query Ledgers](./examples/php/)


 ```php
 <?php

include './ccxt.php';
// include 'Console/Table.php';

date_default_timezone_set('UTC');

// instantiate the exchange by id

$exchange = '\\ccxt\\kraken';
$exchange = new $exchange(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET_KEY',
));

// get ledgers
$ledgers = $exchange->privatePostLedgers ();

// get ledger ids
$ids = array_keys ($ledgers['result']['ledger']);

// get ledger entries for ledger id
$ledger_entries = $exchange->privatePostQueryLedgers(array(
    'id' =>  $ids[0],
));

var_dump ($ledger_entries);

?> 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/kraken-query-ledgers.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 18
- Comment lines: 5
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)
- `Console/Table.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

