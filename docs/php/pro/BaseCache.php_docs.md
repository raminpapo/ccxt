# Documentation: php/pro/BaseCache.php

## File Metadata

- **Path**: `php/pro/BaseCache.php`
- **Size**: 1,702 bytes
- **Lines**: 66
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt\pro;

use SplDoublyLinkedList;

class BaseCache implements \JsonSerializable, \ArrayAccess, \IteratorAggregate, \Countable {
    public $max_size;
    public $deque;

    public function __construct($max_size = null) {
        $this->max_size = $max_size;
        // the deque implemented in Ds has fast shifting by using doubly linked lists
        // https://www.php.net/manual/en/class.ds-deque.php
        // would inherit directly but it is marked as final
        $this->deque = array();
        // default mode
        // $this->deque->setIteratorMode(SplDoublyLinkedList::IT_MODE_FIFO | SplDoublyLinkedList::IT_MODE_KEEP);
    }

    public function getIterator() : \Traversable {
        return new \ArrayObject($this->deque);
    }

    public function JsonSerialize() : array {
        return $this->deque;
    }

    public function count() : int {
        return count($this->deque);
    }

    public function clear() {
        $this->deque = array();
    }

    public function &offsetGet($offset) : mixed {
        return $this->deque[$offset];
    }

    public function offsetSet($index, $newval) : void {
        $this->deque[$index] = $newval;
    }

    public function offsetExists($index) : bool {
        return $index < $this->count();
    }

    public function offsetUnset($index) : void {
        unset($this->deque[$index]);
    }

    public function __toString() {
        return print_r($this->deque, true);
    }

    // meant to be overriden
    public function getLimit($symbol, $limit) {
    }

    // support transpiled snake_case calls
    public function get_limit($symbol, $limit) {
        return $this->getLimit($symbol, $limit);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/pro/BaseCache.php`.

**Classes defined**: BaseCache

**Functions defined**: JsonSerialize, getIterator, offsetSet, __toString, count, __construct, clear, offsetUnset, offsetExists, getLimit



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 43
- Comment lines: 7
- Blank lines: 16

### Main Components

**Functions** (11):
- `JsonSerialize()`
- `__construct()`
- `__toString()`
- `clear()`
- `count()`
- `getIterator()`
- `getLimit()`
- `get_limit()`
- `offsetExists()`
- `offsetSet()`
- `offsetUnset()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/pro/BaseCache.php
```

