# Documentation: go/v4/exchange_queue.go

## File Metadata

- **Path**: `go/v4/exchange_queue.go`
- **Size**: 1,020 bytes
- **Lines**: 66
- **Type**: Go
- **Extension**: .go


## Original Source Code

```go
package ccxt

import (
	"errors"
	"sync"
)

type QueueElement struct {
	Cost float64
	Task chan bool
	Id   string
}

type Queue struct {
	elements []QueueElement
	mu       sync.Mutex
}

func NewQueue() Queue {
	return Queue{
		elements: []QueueElement{},
	}
}

func (q *Queue) Enqueue(element QueueElement) {
	q.mu.Lock()
	defer q.mu.Unlock()
	q.elements = append(q.elements, element)
}

func (q *Queue) Dequeue() (QueueElement, error) {
	q.mu.Lock()
	defer q.mu.Unlock()

	if len(q.elements) == 0 {
		return QueueElement{}, errors.New("queue is empty")
	}

	front := q.elements[0]
	q.elements = q.elements[1:]
	return front, nil
}

func (q *Queue) Length() int {
	q.mu.Lock()
	defer q.mu.Unlock()
	return len(q.elements)
}

func (q *Queue) IsEmpty() bool {
	q.mu.Lock()
	defer q.mu.Unlock()
	return len(q.elements) == 0
}

func (q *Queue) Peek() (QueueElement, error) {
	q.mu.Lock()
	defer q.mu.Unlock()

	if len(q.elements) == 0 {
		return QueueElement{}, errors.New("queue is empty")
	}

	return q.elements[0], nil
}

```

## High-Level Overview

This is a Go file located at `go/v4/exchange_queue.go`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 52
- Comment lines: 0
- Blank lines: 14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Go file:**

