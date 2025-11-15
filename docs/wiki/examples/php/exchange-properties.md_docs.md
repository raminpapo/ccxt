# Documentation: wiki/examples/php/exchange-properties.md

## File Metadata

- **Path**: `wiki/examples/php/exchange-properties.md`
- **Size**: 1,434 bytes
- **Lines**: 65
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Exchange Properties](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchanges = \ccxt\Exchange::$exchanges;

function print_supported_exchanges () {
    $exchanges = \ccxt\Exchange::$exchanges;
    echo 'Supported exchanges: ', implode (', ', $exchanges), "\n";
}

if (count ($argv) > 2) {

    $id = $argv[1];

    $exchange_found = in_array ($id, $exchanges);

    if ($exchange_found) {

        echo 'Instantiating ', $id, ' exchange', "\n";

        $symbol = $argv[2];

        // instantiate the exchange by id
        $exchange = '\\ccxt\\' . $id;
        $exchange = new $exchange(array(
            // 'verbose' => true, // uncomment for debug output
            // set custom headers if needed
            // 'headers' => array(
            //     'YOUR_HEADER' => 'YOUR_VALUE',
            // ),
        ));

        // load all markets from the exchange
        $markets = $exchange->load_markets ();

        // you can also set any of the exchange properties after instantiation
        // $exchange->verbose = true;

        $ticker = $exchange->fetch_ticker ($symbol);

        // output a list of all market symbols
        print_r ($ticker);

    } else {

        echo 'Exchange ', $id, ' not found', "\n";
        print_supported_exchanges ();
    }

} else {

    echo 'Usage: php -f ', __FILE__, ' id symbol', "\n";
    print_supported_exchanges ();

}

?> 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/exchange-properties.md`.

**Functions defined**: print_supported_exchanges



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 32
- Comment lines: 10
- Blank lines: 23

### Main Components

**Functions** (1):
- `print_supported_exchanges()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

