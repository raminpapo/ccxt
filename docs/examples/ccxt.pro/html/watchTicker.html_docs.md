# Documentation: examples/ccxt.pro/html/watchTicker.html

## File Metadata

- **Path**: `examples/ccxt.pro/html/watchTicker.html`
- **Size**: 1,440 bytes
- **Lines**: 52
- **Type**: HTML
- **Extension**: .html


## Original Source Code

```html
<!DOCTYPE HTML>
<html>
<head>
    <title>CCXT Basic example for the browser</title>
    <script type="text/javascript" src="https://unpkg.com/ccxt"></script>
    <script>

        document.addEventListener ("DOMContentLoaded", function () {

            const pollTickerContinuously = async function (exchange, symbol) {

                while (true) {

                    try {

                        const ticker = await exchange.watchTicker (symbol)

                        const text = [
                            exchange.id,
                            symbol,
                            JSON.stringify (ticker, undefined, '\n\t')
                        ]

                        document.getElementById ('content').innerHTML = text.join (' ');

                    } catch (e) {

                        const text = [
                            e.constructor.name,
                            e.message,
                        ]

                        document.getElementById ('content').innerHTML = text.join (' ');

                    }
                }
            }

            const exchange = new ccxt.pro.binance ({ enableRateLimit: true })
            const symbol = 'ETH/BTC'

            pollTickerContinuously (exchange, symbol)
        })
    </script>
</head>
<body>
<h1>Hello, CCXT!</h1>
<p>This example uses websockets to watch changes in price of ETH/BTC</p>
<pre id="content"></pre>
</body>
</html>

```

## High-Level Overview

This is a HTML file located at `examples/ccxt.pro/html/watchTicker.html`.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 38
- Comment lines: 0
- Blank lines: 14

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

