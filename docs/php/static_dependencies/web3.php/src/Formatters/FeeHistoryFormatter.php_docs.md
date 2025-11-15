# Documentation: php/static_dependencies/web3.php/src/Formatters/FeeHistoryFormatter.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Formatters/FeeHistoryFormatter.php`
- **Size**: 1,190 bytes
- **Lines**: 46
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
use Web3\Formatters\BigNumberFormatter;

class FeeHistoryFormatter implements IFormatter
{
    /**
     * format
     * 
     * @param mixed $value
     * @return string
     */
    public static function format($value)
    {
        if (isset($value->oldestBlock)) {
            $value->oldestBlock = BigNumberFormatter::format($value->oldestBlock);
        }
        if (isset($value->baseFeePerGas)) {
            foreach ($value->baseFeePerGas as $key => $baseFeePerGas) {
                $value->baseFeePerGas[$key] = BigNumberFormatter::format($baseFeePerGas);
            }
        }
        if (isset($value->reward)) {
            foreach ($value->reward as $keyOut => $rewards) {
                foreach ($rewards as $keyIn => $reward) {
                    $value->reward[$keyOut][$keyIn] = BigNumberFormatter::format($reward);
                }
            }
        }
        return $value;
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Formatters/FeeHistoryFormatter.php`.

**Classes defined**: FeeHistoryFormatter

**Functions defined**: format

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 42
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
php php/static_dependencies/web3.php/src/Formatters/FeeHistoryFormatter.php
```

