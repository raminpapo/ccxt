# Documentation: wiki/examples/php/symbols.md

## File Metadata

- **Path**: `wiki/examples/php/symbols.md`
- **Size**: 2,328 bytes
- **Lines**: 87
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Symbols](./examples/php/)


 ```php
 <?php

include './ccxt.php';
include 'Console/Table.php';

date_default_timezone_set('UTC');

function style ($s, $style) { return $style . $s . "\033[0m"; }
function green     ($s) { return style ($s, "\033[92m"); }
function blue      ($s) { return style ($s, "\033[94m"); }
function yellow    ($s) { return style ($s, "\033[93m"); }
function red       ($s) { return style ($s, "\033[91m"); }
function pink      ($s) { return style ($s, "\033[95m"); }
function bold      ($s) { return style ($s, "\033[1m"); }
function underline ($s) { return style ($s, "\033[4m"); }
function dump ($s) { echo implode (' ', func_get_args ()) . "\n"; }

$exchanges = \ccxt\Exchange::$exchanges;

function print_supported_exchanges () {
    $exchanges = \ccxt\Exchange::$exchanges;
    dump ('Supported exchanges:', green (implode (', ', $exchanges)));
}

function tabulate ($headers, $rows) {
    $tbl = new Console_Table();
    $tbl->setHeaders ($headers);
    $tbl->addData ($rows);
    return $tbl->getTable ();
}

function market_table_helper ($market) {
    return array (
        $market['id'],
        $market['symbol'],
        $market['base'],
        $market['quote'],
        $market['taker'],
        $market['maker'],
        json_encode ($market['precision']),
        json_encode ($market['limits']),

    );
}

if (count ($argv) > 1) {

    $id = $argv[1];

    $exchange_found = in_array ($id, $exchanges);

    if ($exchange_found) {

        dump ('Instantiating', green ($id), 'exchange');

        // instantiate the exchange by id
        $exchange = '\\ccxt\\' . $id;
        $exchange = new $exchange ();

        // load all markets from the exchange
        $markets = $exchange->load_markets ();

        // output a list of all market symbols
        dump (green ($id), 'has', count ($exchange->symbols), 'symbols:', yellow (implode (', ', $exchange->symbols)));

        // output a table of all markets
        @dump (tabulate(array('id', 'symbol', 'base', 'quote', 'taker', 'maker', 'precision', 'limits'), array_map ('market_table_helper', $markets)));

    } else {

        dump ('Exchange', red ($id), 'not found');
        print_supported_exchanges ();
    }

} else {

    dump ('Usage: php -f', __FILE__,  green ('id'));
    print_supported_exchanges ();

}

?> 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/symbols.md`.

**Functions defined**: green, print_supported_exchanges, red, style, bold, underline, yellow, pink, dump, blue



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 58
- Comment lines: 4
- Blank lines: 25

### Main Components

**Functions** (12):
- `blue()`
- `bold()`
- `dump()`
- `green()`
- `market_table_helper()`
- `pink()`
- `print_supported_exchanges()`
- `red()`
- `style()`
- `tabulate()`
- `underline()`
- `yellow()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)
- `Console/Table.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

