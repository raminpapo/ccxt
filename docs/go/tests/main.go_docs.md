# Documentation: go/tests/main.go

## File Metadata

- **Path**: `go/tests/main.go`
- **Size**: 734 bytes
- **Lines**: 35
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package main

import (
	"fmt"

	"github.com/ccxt/tests/base"
	cache "github.com/ccxt/tests/base/cache"
)

func main() {
	RUN_BASE_TESTS := base.GetCliArgValue("--baseTests")
	WS_TESTS := base.GetCliArgValue("--ws")
	if RUN_BASE_TESTS {
		if WS_TESTS {
			cache.TestWsCache()
			cache.TestWsOrderBook()
			fmt.Println("Base WS tests passed!")
		} else {
			base.BaseTestsInit()
			fmt.Println("Base REST tests passed!")
		}

		return
	}
	tests := base.NewTestMainClass()

	argvExchange := base.GetCliPositionalArg(0)
	argvSymbol := base.GetCliPositionalArg(1)
	argvMethod := base.GetCliPositionalArg(2)

	res := <-tests.Init(argvExchange, argvSymbol, argvMethod)
	base.Print("Got res: " + base.ToString(res))
	base.PanicOnError(res)
}

```

## High-Level Overview

This is a Go file located at `go/tests/main.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 28
- Comment lines: 0
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
