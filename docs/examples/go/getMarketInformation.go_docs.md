# Documentation: examples/go/getMarketInformation.go

## File Metadata

- **Path**: `examples/go/getMarketInformation.go`
- **Size**: 475 bytes
- **Lines**: 29
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"ccxt/go/ccxt"
)

func GetMarket() {
	// instantiate the exchange
	exchange := ccxt.NewBinance(nil)

	exchange.LoadMarkets() // loading markets first

	symbol := "BTC/USDT"

	market := exchange.GetMarket(symbol)

	if *market.Spot {
		println("Spot market")
	} else if *market.Swap {
		println("Swap market")
	}

	swapSymbol := "BTC/USDT:USDT"

	swapMarket := exchange.GetMarket(swapSymbol)

	println("Contract Size: ", *swapMarket.ContractSize)
}

```

## High-Level Overview

This is a Go file located at `examples/go/getMarketInformation.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 18
- Comment lines: 1
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

