# Documentation: examples/go/watch-multiple-exchanges.go

## File Metadata

- **Path**: `examples/go/watch-multiple-exchanges.go`
- **Size**: 814 bytes
- **Lines**: 42
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"fmt"
	"log"
	"sync"

	ccxtpro "github.com/ccxt/ccxt/go/v4/pro"
)

var wg sync.WaitGroup

func watchTrades(exchange ccxtpro.IExchange, symbol string) {
	defer wg.Done()
	for {
		trades, err := exchange.WatchTrades(symbol)
		if err != nil {
			log.Printf("Error watching trades for %s on %s: %v", symbol, exchange.GetId(), err)
			break
		}
		fmt.Println("Exchange", exchange.GetId(), "Symbol", symbol, "Trades:", len(trades))
	}
}

func WatchMultiple() {

	exchangesNames := []string{"binance", "bybit"}
	symbol := "BTC/USDT"

	for _, exchangeName := range exchangesNames {
		exchange := ccxtpro.CreateExchange(exchangeName, nil)
		if exchange == nil {
			log.Printf("Exchange %s not found", exchangeName)
			continue
		}
		wg.Add(1)
		go watchTrades(exchange, symbol)
	}

	wg.Wait()
}

```

## High-Level Overview

This is a Go file located at `examples/go/watch-multiple-exchanges.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 33
- Comment lines: 0
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

