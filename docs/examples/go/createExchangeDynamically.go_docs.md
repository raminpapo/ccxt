# Documentation: examples/go/createExchangeDynamically.go

## File Metadata

- **Path**: `examples/go/createExchangeDynamically.go`
- **Size**: 389 bytes
- **Lines**: 19
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package main

import (
	"ccxt/go/ccxt"
	"fmt"
)

func AbstractExchangeCreation() {
	// instantiate the exchange
	exchanges := []string{"binance", "bybit", "okx"}
	symbol := "BTC/USDT"
	for _, exchangeName := range exchanges {
		exchange := ccxt.CreateExchange(exchangeName, nil)

		ticker, _ := exchange.FetchTicker(symbol)
		fmt.Println("Ticker for", exchangeName, ":", ticker.Last)
	}
}

```

## High-Level Overview

This is a Go file located at `examples/go/createExchangeDynamically.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 14
- Comment lines: 1
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

