# Documentation: examples/go/createOrderWithParams.go

## File Metadata

- **Path**: `examples/go/createOrderWithParams.go`
- **Size**: 714 bytes
- **Lines**: 35
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package examples

import (
	"ccxt/go/ccxt"
	"fmt"
)

func CreateOrder() {
	// instantiate the exchange
	exchange := ccxt.NewBinance(nil)

	// set apiKey and secret
	exchange.ApiKey = "my-api-key"
	exchange.Secret = "my secret"

	// if in sandbox mode run this line
	// exchange.SetSandboxMode(true)

	// We will create a limit order that is also postOnly

	orderParams := map[string]interface{}{
		"postOnly":      true,
		"clientOrderId": "my-client-order-id",
	}

	order, err := exchange.CreateOrder("BTC/USDT", "limit", "buy", 0.001, ccxt.WithCreateOrderPrice(10000), ccxt.WithCreateOrderParams(orderParams))

	if err != nil {
		fmt.Print(err) // order failed check the error
		return
	}

	fmt.Println(order)
}

```

## High-Level Overview

This is a Go file located at `examples/go/createOrderWithParams.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 20
- Comment lines: 5
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Security Considerations

- ⚠️ Possible hardcoded API key



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

