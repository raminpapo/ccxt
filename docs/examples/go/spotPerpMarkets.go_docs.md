# Documentation: examples/go/spotPerpMarkets.go

## File Metadata

- **Path**: `examples/go/spotPerpMarkets.go`
- **Size**: 519 bytes
- **Lines**: 31
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"ccxt/go/ccxt"
	"fmt"
)

func spotPerpMarkets() {
	exchange := ccxt.NewBybit(nil)
	exchange.ApiKey = ""
	exchange.Secret = ""

	exchange.LoadMarkets()

	allMarkets := exchange.GetMarketsList()

	spotMarkets := []string{}
	swapMarkets := []string{}

	for _, elem := range allMarkets {
		if *elem.Spot {
			spotMarkets = append(spotMarkets, *elem.Symbol)
		} else if *elem.Swap {
			swapMarkets = append(swapMarkets, *elem.Symbol)
		}
	}

	fmt.Println(spotMarkets)
	fmt.Println(swapMarkets)
}

```

## High-Level Overview

This is a Go file located at `examples/go/spotPerpMarkets.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 23
- Comment lines: 0
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

