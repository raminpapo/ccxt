# Documentation: examples/go/setMarketsFromExchange.go

## File Metadata

- **Path**: `examples/go/setMarketsFromExchange.go`
- **Size**: 1,444 bytes
- **Lines**: 53
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"ccxt/go/ccxt"
	"fmt"
	"runtime"
	"runtime/debug"
)

func getMemoryUsage() float64 {
	// Force garbage collection to get accurate memory stats
	runtime.GC()
	debug.FreeOSMemory()

	var m runtime.MemStats
	runtime.ReadMemStats(&m)

	// Convert bytes to MB
	return float64(m.Alloc) / 1024 / 1024
}

func main() {
	fmt.Printf("Initial memory usage: %.2f MB\n", getMemoryUsage())

	// Create first binance exchange
	binance := ccxt.NewBinance(nil)
	fmt.Printf("Memory usage after creating binance: %.2f MB\n", getMemoryUsage())

	// Load markets for first exchange
	markets, err := binance.LoadMarkets()
	if err != nil {
		fmt.Printf("Failed to load markets for first exchange: %v\n", err)
		return
	}
	if markets == nil {
		fmt.Println("Failed to load markets for first exchange")
		return
	}
	fmt.Printf("Memory usage after loading markets: %.2f MB\n", getMemoryUsage())

	// Create second binance exchange
	binance2 := ccxt.NewBinance(nil)
	fmt.Printf("Memory usage after creating binance2: %.2f MB\n", getMemoryUsage())

	binance2.SetMarketsFromExchange(binance)
	fmt.Printf("Memory usage after setting markets from exchange: %.2f MB\n", getMemoryUsage())
	fmt.Printf("binance2.symbols loaded: %d\n", len(binance2.GetSymbols()))

	// Note: Go doesn't have explicit close methods like Python's async close
	// The garbage collector will handle cleanup
	fmt.Printf("Final memory usage: %.2f MB\n", getMemoryUsage())
}

```

## High-Level Overview

This is a Go file located at `examples/go/setMarketsFromExchange.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 35
- Comment lines: 7
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

