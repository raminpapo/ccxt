# Documentation: php/static_dependencies/web3.php/src/Formatters/HexFormatter.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Formatters/HexFormatter.php`
- **Size**: 701 bytes
- **Lines**: 36
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

class HexFormatter implements IFormatter
{
    /**
     * format
     * 
     * @param mixed $value
     * @return string
     */
    public static function format($value)
    {
        if (is_string($value) && Utils::isZeroPrefixed($value)) {
            $value = mb_strtolower($value);
            return $value;
        } else {
            $value = Utils::toHex($value, true);
        }
        return $value;
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Formatters/HexFormatter.php`.

**Classes defined**: HexFormatter

**Functions defined**: format

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 32
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
php php/static_dependencies/web3.php/src/Formatters/HexFormatter.php
```

