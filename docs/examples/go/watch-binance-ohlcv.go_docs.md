# Documentation: examples/go/watch-binance-ohlcv.go

## File Metadata

- **Path**: `examples/go/watch-binance-ohlcv.go`
- **Size**: 427 bytes
- **Lines**: 25
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"fmt"
	"log"

	ccxtpro "github.com/ccxt/ccxt/go/v4/pro"
)

func WatchOHLCV() {

	binance := ccxtpro.NewBinance(nil)

	symbol := "BTC/USDT"

	for {
		ohlcv, err := binance.WatchOHLCV(symbol, ccxtpro.WithWatchOHLCVTimeframe("1h"))
		if err != nil {
			log.Printf("Error watching OHLCV for %s on %s: %v", symbol, binance.GetId(), err)
			break
		}
		fmt.Println("Symbol", symbol, "OHLCV:", ohlcv)
	}
}

```

## High-Level Overview

This is a Go file located at `examples/go/watch-binance-ohlcv.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 18
- Comment lines: 0
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

