# Documentation: php/pro/ArrayCacheByTimestamp.php

## File Metadata

- **Path**: `php/pro/ArrayCacheByTimestamp.php`
- **Size**: 1,511 bytes
- **Lines**: 50
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt\pro;

class ArrayCacheByTimestamp extends BaseCache {
    public $hashmap;
    private $size_tracker;
    public $new_updates;
    public $clear_updates;

    public function __construct($max_size = null) {
        parent::__construct($max_size);
        $this->hashmap = array();
        $this->size_tracker = array();
        $this->new_updates = 0;
        $this->clear_updates = false;
    }

    public function getLimit($symbol, $limit) {
        $this->clear_updates = true;
        if ($limit === null) {
            return $this->new_updates;
        }
        return min($this->new_updates, $limit);
    }

    public function append($item) {
        if (array_key_exists($item[0], $this->hashmap)) {
            $prev_ref = &$this->hashmap[$item[0]];
            # updates the reference
            $prev_ref = $item;
        } else {
            $this->hashmap[$item[0]] = &$item;
            if (count($this->deque) === $this->max_size) {
                $delete_reference = array_shift($this->deque);
                unset($this->hashmap[$delete_reference[0]]);
            }
            # this allows us to effectively pass by reference
            //array_push($this->deque->push(null);
            $this->deque[] = &$item;
        }
        if ($this->clear_updates) {
            $this->clear_updates = false;
            $this->size_tracker = array();
        }
        $this->size_tracker[$item[0]] = 1;
        $this->new_updates = count($this->size_tracker);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/pro/ArrayCacheByTimestamp.php`.

**Classes defined**: ArrayCacheByTimestamp

**Functions defined**: append, __construct, getLimit



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 41
- Comment lines: 3
- Blank lines: 6

### Main Components

**Functions** (3):
- `__construct()`
- `append()`
- `getLimit()`



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
php php/pro/ArrayCacheByTimestamp.php
```

