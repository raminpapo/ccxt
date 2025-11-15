# Documentation: examples/go/bybit-place-order-ws.go

## File Metadata

- **Path**: `examples/go/bybit-place-order-ws.go`
- **Size**: 474 bytes
- **Lines**: 25
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"fmt"
	"log"

	ccxt "github.com/ccxt/ccxt/go/v4"
	ccxtpro "github.com/ccxt/ccxt/go/v4/pro"
)

func PlaceOrderWs() {

	bybit := ccxtpro.NewBybit(nil)

	symbol := "BTC/USDT"

	bybit.LoadMarkets()

	order, err := bybit.CreateOrderWs(symbol, "limit", "buy", 0.001, ccxt.WithCreateOrderWsPrice(2000))
	if err != nil {
		log.Printf("Error creating order for %s on %s: %v", symbol, bybit.GetId(), err)
		return
	}
	fmt.Println("Order created:", order)
}
```

## High-Level Overview

This is a Go file located at `examples/go/bybit-place-order-ws.go`.

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

