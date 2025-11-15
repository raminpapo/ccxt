# Documentation: php/static_dependencies/web3.php/src/Formatters/TransactionFormatter.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Formatters/TransactionFormatter.php`
- **Size**: 1,174 bytes
- **Lines**: 47
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

/**
 * This file is part of web3.php package.
 * 
 * (c) Kuan-Cheng,Lai <alk03073135@gmail.com>
 * 
 * @author Peter Lai <alk03073135@gmail.com>
 * @license MIT
 */

namespace Web3\Formatters;

use InvalidArgumentException;
use Web3\Utils;
use Web3\Formatters\IFormatter;
use Web3\Formatters\HexFormatter;
use Web3\Formatters\QuantityFormatter;

class TransactionFormatter implements IFormatter
{
    /**
     * format
     * 
     * @param mixed $value
     * @return string
     */
    public static function format($value)
    {
        if (isset($value['gas'])) {
            $value['gas'] = QuantityFormatter::format($value['gas']);
        }
        if (isset($value['gasPrice'])) {
            $value['gasPrice'] = QuantityFormatter::format($value['gasPrice']);
        }
        if (isset($value['value'])) {
            $value['value'] = QuantityFormatter::format($value['value']);
        }
        if (isset($value['data'])) {
            $value['data'] = HexFormatter::format($value['data']);
        }
        if (isset($value['nonce'])) {
            $value['nonce'] = QuantityFormatter::format($value['nonce']);
        }
        return $value;
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Formatters/TransactionFormatter.php`.

**Classes defined**: TransactionFormatter

**Functions defined**: format

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 43
- Comment lines: 14
- Blank lines: -10

### Main Components

**Functions** (1):
- `format()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/web3.php/src/Formatters/TransactionFormatter.php
```

