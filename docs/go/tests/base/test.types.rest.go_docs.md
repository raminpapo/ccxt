# Documentation: go/tests/base/test.types.rest.go

## File Metadata

- **Path**: `go/tests/base/test.types.rest.go`
- **Size**: 595 bytes
- **Lines**: 22
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package base

import ccxt "github.com/ccxt/ccxt/go/v4"

// this test ensures we have all types defined in ccxt, alias exchanges, etc

func TestTypesRest() {

	binanceExchange := ccxt.NewBinance(nil)

	_, _ = binanceExchange.FetchTrades("BTC/USDT", ccxt.WithFetchTradesLimit(5))

	binanceI := ccxt.CreateExchange("binance", nil)

	_, _ = binanceI.FetchTrades("BTC/USDT", ccxt.WithFetchTradesLimit(5))

	myokx := ccxt.NewMyokx(nil)

	_, _ = myokx.FetchOrder("iddd", ccxt.WithFetchOrderSymbol("BTC/USDT")) // ensure myokx has access to a method that does not implement directly, like fetchOrder

}

```

## High-Level Overview

This is a Go file located at `go/tests/base/test.types.rest.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 10
- Comment lines: 1
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `github.com/ccxt/ccxt/go/v4` (imported)



## Testing & Execution

This appears to be a test file.

**To run this test:**
