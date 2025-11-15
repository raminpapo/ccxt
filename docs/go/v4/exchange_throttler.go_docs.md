# Documentation: go/v4/exchange_throttler.go

## File Metadata

- **Path**: `go/v4/exchange_throttler.go`
- **Size**: 1,818 bytes
- **Lines**: 98
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package ccxt

import (
	"time"

	u "github.com/google/uuid"
)

type Throttler struct {
	Queue   Queue
	Running bool
	Config  map[string]interface{}
}

func NewThrottler(config map[string]interface{}) *Throttler {
	defaultConfig := map[string]interface{}{
		"refillRate":  1.0,
		"delay":       0.001,
		"capacity":    1.0,
		"maxCapacity": 2000,
		"tokens":      0,
		"cost":        1.0,
	}

	return &Throttler{
		Queue:   NewQueue(),
		Running: false,
		Config:  ExtendMap(defaultConfig, config),
	}
}

func (t *Throttler) Throttle(cost2 interface{}) <-chan bool {
	if cost2 == nil {
		cost2 = t.Config["cost"]
	}
	cost := ToFloat64(cost2)
	task := make(chan bool)

	queueElement := QueueElement{
		Cost: cost,
		Task: task,
		Id:   u.New().String(),
	}

	t.Queue.Enqueue(queueElement)

	if !t.Running {
		t.Running = true
		go t.Loop()
	}

	return task
}

func (t *Throttler) Loop() {

	lastTimestamp := Milliseconds()
	for t.Running {
		if t.Queue.IsEmpty() {
			t.Running = false
			continue
		}
		first, _ := t.Queue.Peek()
		task := first.Task
		cost := first.Cost

		tokens := ToFloat64(t.Config["tokens"])

		if tokens >= 0 {
			t.Config["tokens"] = tokens - cost

			if task != nil {
				task <- true
				close(task)
			}
			t.Queue.Dequeue()

			if t.Queue.IsEmpty() {
				t.Running = false
			}
		} else {
			sleepTime := ToFloat64(t.Config["delay"]) * 1000
			time.Sleep(time.Duration(sleepTime) * time.Millisecond)
			current := Milliseconds()
			elapsed := current - lastTimestamp
			lastTimestamp = current
			sumTokens := ToFloat64(t.Config["refillRate"]) * ToFloat64(elapsed)
			tokens := ToFloat64(t.Config["tokens"]) + sumTokens
			t.Config["tokens"] = MathMin(tokens, ToFloat64(t.Config["capacity"]))
		}
	}

}

func Milliseconds() int64 {
	return time.Now().UnixNano() / int64(time.Millisecond)
}

```

## High-Level Overview

This is a Go file located at `go/v4/exchange_throttler.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 98
- Code lines: 79
- Comment lines: 0
- Blank lines: 19

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

