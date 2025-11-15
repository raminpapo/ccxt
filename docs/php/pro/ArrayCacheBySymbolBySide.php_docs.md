# Documentation: php/pro/ArrayCacheBySymbolBySide.php

## File Metadata

- **Path**: `php/pro/ArrayCacheBySymbolBySide.php`
- **Size**: 2,403 bytes
- **Lines**: 62
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt\pro;

class ArrayCacheBySymbolBySide extends ArrayCache {
    public $hashmap;
    private $index;

    public function __construct($max_size = null) {
        parent::__construct($max_size);
        $this->nested_new_updates_by_symbol = true;
        $this->hashmap = array();
        $this->index = array();
    }

    public function append($item) {
        if (array_key_exists($item['symbol'], $this->hashmap)) {
            $by_side = &$this->hashmap[$item['symbol']];
        } else {
            $by_side = array();
            $this->hashmap[$item['symbol']] = &$by_side;
        }
        if (array_key_exists($item['side'], $by_side)) {
            $prev_ref = &$by_side[$item['side']];
            # updates the reference
            $prev_ref = $item;
            $item = &$prev_ref;
            $index = array_search($item['symbol'] . $item['side'], $this->index);
            array_splice($this->index, $index, 1);
            array_splice($this->deque, $index, 1);
        } else {
            $by_side[$item['side']] = &$item;
            if (count($this->deque) === $this->max_size) {
                $delete_item = array_shift($this->deque);
                array_shift($this->index);
                unset($this->hashmap[$delete_item['symbol']][$delete_item['side']]);
            }
        }
        # this allows us to effectively pass by reference
        $this->deque[] = &$item;
        $this->index[] = $item['symbol'] . $item['side'];
        if ($this->clear_all_updates) {
            $this->clear_all_updates = false;
            $this->clear_updates_by_symbol = array();
            $this->all_new_updates = 0;
            $this->new_updates_by_symbol = array();
        }
        if (!array_key_exists($item['symbol'], $this->new_updates_by_symbol)) {
            $this->new_updates_by_symbol[$item['symbol']] = array();
        }
        if ($this->clear_updates_by_symbol[$item['symbol']] ?? false) {
            $this->clear_updates_by_symbol[$item['symbol']] = false;
            $this->new_updates_by_symbol[$item['symbol']] = array();
        }
        $side_set = &$this->new_updates_by_symbol[$item['symbol']];
        $before_length = count($side_set);
        $side_set[$item['side']] = 1;
        $after_length = count($side_set);
        $this->all_new_updates = ($this->all_new_updates ?? 0) + ($after_length - $before_length);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/pro/ArrayCacheBySymbolBySide.php`.

**Classes defined**: ArrayCacheBySymbolBySide

**Functions defined**: append, __construct



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 55
- Comment lines: 2
- Blank lines: 5

### Main Components

**Functions** (2):
- `__construct()`
- `append()`



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
php php/pro/ArrayCacheBySymbolBySide.php
```

