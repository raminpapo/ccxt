# Documentation: php/static_dependencies/starknet.php/src/Cairo/Felt.php

## File Metadata

- **Path**: `php/static_dependencies/starknet.php/src/Cairo/Felt.php`
- **Size**: 2,060 bytes
- **Lines**: 74
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
/**
 * This file is part of starknet.php package.
 * 
 * (c) Kuan-Cheng,Lai <alk03073135@gmail.com>
 * 
 * @author Peter Lai <alk03073135@gmail.com>
 * @license MIT
 */

namespace StarkNet\Cairo;

use InvalidArgumentException;
use phpseclib\Math\BigInteger as BigNumber;
use StarkNet\Utils;
use StarkNet\Constants;

class Felt
{
    /**
     * assertInCairoVMRange
     * 
     * @param string|BigNumber $value
     * @return void
     */
    public static function assertInCairoVMRange($value)
    {
        if (is_string($value)) {
            $value = Utils::toBn($value);
        } elseif (!($value instanceof BigNumber)) {
            throw new InvalidArgumentException('The value to assertInCairoVMRange function in not support.');
        }
        if (
            !($value->compare(Constants::ZERO()) >= 0 && $value->compare(Utils::toBn(Constants::FIELD_PRIME)) < 0)
        ) {
            throw new InvalidArgumentException('The value in expected to be in the range [0,' . Constants::FIELD_PRIME . '].');
        }
    }

    /**
     * encodeShortString
     * 
     * @param string $value
     * @return string
     */
    public static function encodeShortString($value)
    {
        if (!is_string($value)) {
            throw new InvalidArgumentException('The value to encodeShortString function must be string.');
        }
        if (mb_strlen($value) > 31) {
            throw new InvalidArgumentException('Shortstring cannot be longer than 31 characters.');
        }
        $value = Utils::toHex($value);
        self::assertInCairoVMRange($value);
        return $value;
    }

    /**
     * decodeShortString
     * 
     * @param string $value
     * @return string
     */
    public static function decodeShortString($value)
    {
        if (!is_string($value)) {
            throw new InvalidArgumentException('The value to decodeShortString function must be string.');
        }
        self::assertInCairoVMRange($value);
        // allowed 31 characters
        return mb_substr(Utils::hexToBin($value), 0, 31);
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/starknet.php/src/Cairo/Felt.php`.

**Classes defined**: Felt

**Functions defined**: in, must, encodeShortString, decodeShortString, assertInCairoVMRange

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 74
- Code lines: 68
- Comment lines: 27
- Blank lines: -21

### Main Components

**Classes** (1):
- `Felt`

**Functions** (5):
- `assertInCairoVMRange()`
- `decodeShortString()`
- `encodeShortString()`
- `in()`
- `must()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/starknet.php/src/Cairo/Felt.php
```

