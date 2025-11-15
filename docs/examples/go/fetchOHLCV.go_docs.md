# Documentation: examples/go/fetchOHLCV.go

## File Metadata

- **Path**: `examples/go/fetchOHLCV.go`
- **Size**: 426 bytes
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

func FetchOHLCV() {
	// instantiate the exchange
	exchange := ccxt.NewBinance(nil)

	// Since fetchOHLCV is public you don't need to set apiKey and secret

	ohlcv, err := exchange.FetchOHLCV("BTC/USDT", ccxt.WithFetchOHLCVTimeframe("1m"), ccxt.WithFetchOHLCVLimit(10))

	if err != nil {
		fmt.Print(err) // request failed check the error
		return
	}

	fmt.Println(ohlcv)
}

```

## High-Level Overview

This is a Go file located at `examples/go/fetchOHLCV.go`.

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

