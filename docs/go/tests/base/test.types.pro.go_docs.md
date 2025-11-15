# Documentation: go/tests/base/test.types.pro.go

## File Metadata

- **Path**: `go/tests/base/test.types.pro.go`
- **Size**: 684 bytes
- **Lines**: 24
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package base

import (
	ccxtpro "github.com/ccxt/ccxt/go/v4/pro"
)

// this test ensures we have all types defined in ccxtpro and we don't need to import ccxt just for types
// this function does not need to be called, it's just for type checking

func TestTypesPro() {

	binanceExchange := ccxtpro.NewBinance(nil)

	_, _ = binanceExchange.WatchTrades("BTC/USDT", ccxtpro.WithWatchTradesLimit(5))

	_, _ = binanceExchange.FetchTrades("BTC/USDT", ccxtpro.WithFetchTradesLimit(5))

	binanceI := ccxtpro.CreateExchange("binance", nil)

	_, _ = binanceI.WatchTrades("BTC/USDT", ccxtpro.WithWatchTradesLimit(5))

	_, _ = binanceI.FetchTrades("BTC/USDT", ccxtpro.WithFetchTradesLimit(5))
}

```

## High-Level Overview

This is a Go file located at `go/tests/base/test.types.pro.go`.

**Functions defined**: does

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 12
- Comment lines: 2
- Blank lines: 10

### Main Components

**Functions** (1):
- `does()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
