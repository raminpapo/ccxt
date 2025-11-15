# Documentation: examples/html/basic-inheritance.html

## File Metadata

- **Path**: `examples/html/basic-inheritance.html`
- **Size**: 1,367 bytes
- **Lines**: 47
- **Type**: HTML
- **Extension**: .html


## Original Source Code

```html
<!DOCTYPE HTML>
<html>
<head>
    <title>CCXT Basic example for the browser</title>
    <script type="text/javascript" src="https://unpkg.com/ccxt"></script>
    <style type="text/css">
        #contentA { background-color: #ccccff; }
        #contentB { background-color: #ffcccc; }
    </style>
    <script>'use strict'

        class MyExchange extends ccxt.coinbasepro {

            async fetchTicker (symbol, params = {}) {
                alert ("I'm about to call the parent method from the overrided class, woohooo!")
                // just call the parent method and that's it
                return super.fetchTicker (symbol, params);
            }
        }

        document.addEventListener ("DOMContentLoaded", function () {

            const exchange = new MyExchange ()

            const symbol = 'ETH/BTC'

            const showFetchedTicker = function (ticker, elementId) {

                const text = [
                    exchange.id,
                    symbol,
                    JSON.stringify (ticker, undefined, '\n\t')
                ]

                document.getElementById (elementId).innerHTML = text.join (' ')

            }

            exchange.fetchTicker (symbol).then (ticker => showFetchedTicker (ticker, 'content'))
        })
    </script>
</head>
<body>
<h1>Hello, CCXT!</h1>
<pre id="content"></pre>
</body>
</html>
```

## High-Level Overview

This is a HTML file located at `examples/html/basic-inheritance.html`.

**Classes defined**: MyExchange



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 34
- Comment lines: 3
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this HTML file:**

