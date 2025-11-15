# Documentation: php/pro/ArrayCache.php

## File Metadata

- **Path**: `php/pro/ArrayCache.php`
- **Size**: 2,192 bytes
- **Lines**: 64
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt\pro;

class ArrayCache extends BaseCache {
    public $new_updates_by_symbol;
    public $clear_updates_by_symbol;
    public $nested_new_updates_by_symbol;
    public $all_new_updates;
    public $clear_all_updates;

    public function __construct($max_size = null) {
        parent::__construct($max_size);
        $this->nested_new_updates_by_symbol = false;
        $this->new_updates_by_symbol = array();
        $this->clear_updates_by_symbol = array();
        $this->all_new_updates = 0;
        $this->clear_all_updates = false;
    }

    public function getLimit($symbol, $limit) {
        $new_updates_value = null;

        if ($symbol === null) {
            $new_updates_value = $this->all_new_updates;
            $this->clear_all_updates = true;
        } else {
            $new_updates_value = $this->new_updates_by_symbol[$symbol];
            if (($new_updates_value !== null) && $this->nested_new_updates_by_symbol) {
                $new_updates_value = count($new_updates_value);
            }
            $this->clear_updates_by_symbol[$symbol] = true;
        }

        if ($new_updates_value === null) {
            return $limit;
        }
        else if ($limit !== null) {
            return min($new_updates_value, $limit);
        } else {
            return $new_updates_value;
        }
    }

    public function append($item) {
        if ($this->max_size && (count($this->deque) === $this->max_size)) {
            array_shift($this->deque);
        }
        $this->deque[] = $item;
        if ($this->clear_all_updates) {
            $this->clear_all_updates = false;
            $this->clear_updates_by_symbol = array();
            $this->all_new_updates = 0;
            $this->new_updates_by_symbol = array();
        }
        if ($this->clear_updates_by_symbol[$item['symbol']] ?? false) {
            $this->clear_updates_by_symbol[$item['symbol']] = false;
            $this->new_updates_by_symbol[$item['symbol']] = 0;
        }
        $this->new_updates_by_symbol[$item['symbol']] = ($this->new_updates_by_symbol[$item['symbol']] ?? 0) + 1;
        $this->all_new_updates = ($this->all_new_updates ?? 0) + 1;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/pro/ArrayCache.php`.

**Classes defined**: ArrayCache

**Functions defined**: append, __construct, getLimit



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 56
- Comment lines: 0
- Blank lines: 8

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
php php/pro/ArrayCache.php
```

