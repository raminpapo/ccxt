# Documentation: examples/html/binance-cors-proxy.html

## File Metadata

- **Path**: `examples/html/binance-cors-proxy.html`
- **Size**: 759 bytes
- **Lines**: 29
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

            async function main () {
                const exchange = new ccxt.binance ({
                    'apiKey': 'YOUR_API_KEY',
                    'secret': 'YOUR_API_SECRET',
                    'proxyUrl': 'https://cors-anywhere.herokuapp.com/',
                })
                const response = await exchange.fetchBalance ()
                console.log (response)
            }

            main ()
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

This is a HTML file located at `examples/html/binance-cors-proxy.html`.

**Functions defined**: main



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 25
- Comment lines: 0
- Blank lines: 4

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this HTML file:**

