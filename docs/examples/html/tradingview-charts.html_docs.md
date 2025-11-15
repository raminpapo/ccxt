# Documentation: examples/html/tradingview-charts.html

## File Metadata

- **Path**: `examples/html/tradingview-charts.html`
- **Size**: 2,480 bytes
- **Lines**: 62
- **Type**: HTML
- **Extension**: .html


## Original Source Code

```html
<!DOCTYPE HTML>
<html>
<head>
    <title>CCXT Basic example for the browser</title>
    <script type="text/javascript" src="https://unpkg.com/ccxt"></script>
    <script type="text/javascript" src="https://unpkg.com/lightweight-charts@3.4.0/dist/lightweight-charts.standalone.production.js"></script>
    <script>

        document.addEventListener ("DOMContentLoaded", async function () {

            try {
                const exchange = new ccxt.coinbasepro ({ enableRateLimit: true });
                const symbol = 'ETH/BTC';
                const timeframe = '1d';
                const since = undefined;
                const limit = 600;
                const config = {
                    width: 600,
                    height: 300,
                    priceScale: {
                        position: 'left',
                        mode: 1,
                        autoScale: true,
                        invertScale: false,
                    },
                    timeScale: {
                        fixLeftEdge: true,
                        lockVisibleTimeRangeOnResize: true,
                        rightBarStaysOnScroll: true,
                        visible: true,
                        timeVisible: true,
                        secondsVisible: true,
                    },
                    crosshair: {
                        mode: window.LightweightCharts.CrosshairMode.Normal,
                    },
                };
                const chart = window.LightweightCharts.createChart(document.body, config);
                const candleSeries = chart.addCandlestickSeries();
                while (true) {
                    try {
                        const response = await exchange.fetchOHLCV(symbol, timeframe, since, limit);
                        const last = response[response.length - 1]
                        const [ timestamp, open, high, low, close ] = last;
                        const data = response.map (([ timestamp, open, high, low, close ]) => ({ time: exchange.iso8601 (timestamp), open, high, low, close }));
                        candleSeries.setData(data);
                    } catch (e) {
                        console.log (e.constructor.name, e.message);
                    }
                    await exchange.sleep (1000);
                }
            } catch (e) {
                alert (e.constructor.name + ' ' + e.message);
            }

        })
    </script>
</head>
<body>
</body>
</html>

```

## High-Level Overview

This is a HTML file located at `examples/html/tradingview-charts.html`.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 58
- Comment lines: 0
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `https://unpkg.com/lightweight-charts@3.4.0/dist/lightweight-charts.standalone.production.js` (referenced)



## Testing & Execution

**To execute this HTML file:**

