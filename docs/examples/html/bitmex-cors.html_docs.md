# Documentation: examples/html/bitmex-cors.html

## File Metadata

- **Path**: `examples/html/bitmex-cors.html`
- **Size**: 1,119 bytes
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
    <script>

        document.addEventListener ("DOMContentLoaded", function () {

            alert ('ccxt version ' + ccxt.version);

            const exchange = new ccxt.bitmex ({
                'proxyUrl': 'http://127.0.0.1:8080/',
            })

            const symbol = 'BTC/USDT'

            exchange.fetchTicker (symbol).then (ticker => {

                const text = [
                    exchange.id,
                    symbol,
                    JSON.stringify (ticker, undefined, '\n\t')
                ]

                document.getElementById ('content').innerHTML = text.join (' ')

            }).catch (e => {

                const text = [
                    e.constructor.name,
                    e.message,
                ]

                document.getElementById ('content').innerHTML = text.join (' ')

            })

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

This is a HTML file located at `examples/html/bitmex-cors.html`.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 34
- Comment lines: 0
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this HTML file:**

