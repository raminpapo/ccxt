# Documentation: examples/html/basic-poller.html

## File Metadata

- **Path**: `examples/html/basic-poller.html`
- **Size**: 1,433 bytes
- **Lines**: 53
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

            alert ('ccxt version ' + ccxt.version + ' supporting ');

            const pollTickerContinuously = async function (exchange, symbol) {

                while (true) {

                    try {

                        const ticker = await exchange.fetchTicker (symbol)

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

            const exchange = new ccxt.binance ({ enableRateLimit: true })
            const symbol = 'ETH/BTC'

            pollTickerContinuously (exchange, symbol)
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

This is a HTML file located at `examples/html/basic-poller.html`.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 38
- Comment lines: 0
- Blank lines: 15

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

