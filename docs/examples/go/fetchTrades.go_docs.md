# Documentation: examples/go/fetchTrades.go

## File Metadata

- **Path**: `examples/go/fetchTrades.go`
- **Size**: 396 bytes
- **Lines**: 23
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"ccxt/go/ccxt"
	"fmt"
)

func FetchTrades() {
	// instantiate the exchange
	exchange := ccxt.NewBinance(nil)

	// Since fetchTrades is public you don't need to set apiKey and secret

	trades, err := exchange.FetchTrades("BTC/USDT", ccxt.WithFetchTradesLimit(50))

	if err != nil {
		fmt.Print(err) // request failed check the error
		return
	}

	fmt.Println(trades)
}

```

## High-Level Overview

This is a Go file located at `examples/go/fetchTrades.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 14
- Comment lines: 2
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

