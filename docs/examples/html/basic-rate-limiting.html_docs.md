# Documentation: examples/html/basic-rate-limiting.html

## File Metadata

- **Path**: `examples/html/basic-rate-limiting.html`
- **Size**: 1,192 bytes
- **Lines**: 50
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

        document.addEventListener ("DOMContentLoaded", async function () {

            alert ('ccxt version ' + ccxt.version);

            const enableRateLimit = true
            const exchange = new ccxt.poloniex ({ enableRateLimit })
            const symbol = 'ETH/BTC'

            while (true) {

                let text = []

                try {

                    const ticker = await exchange.fetchTicker (symbol)

                    text = [
                        exchange.id,
                        symbol,
                        JSON.stringify (exchange.omit (ticker, 'info'), undefined, '\t')
                    ]

                } catch (e) {

                    text = [
                        e.constructor.name,
                        e.message,
                    ]
                }

                document.getElementById ('content').innerHTML = text.join (' ')

            }

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

This is a HTML file located at `examples/html/basic-rate-limiting.html`.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 36
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

