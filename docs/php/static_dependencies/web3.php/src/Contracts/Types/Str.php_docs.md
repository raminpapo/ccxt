# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/Str.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/Str.php`
- **Size**: 2,131 bytes
- **Lines**: 94
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

namespace Web3\Contracts\Types;

use Web3\Utils;
use Web3\Contracts\SolidityType;
use Web3\Contracts\Types\IType;
use Web3\Formatters\IntegerFormatter;
use Web3\Formatters\BigNumberFormatter;

class Str extends SolidityType implements IType
{
    /**
     * construct
     * 
     * @return void
     */
    public function __construct()
    {
        //
    }

    /**
     * isType
     * 
     * @param string $name
     * @return bool
     */
    public function isType($name)
    {
        return (preg_match('/^string/', $name) === 1);
    }

    /**
     * isDynamicType
     * 
     * @return bool
     */
    public function isDynamicType()
    {
        return true;
    }

    /**
     * inputFormat
     * 
     * @param mixed $value
     * @param array $abiType
     * @return string
     */
    public function inputFormat($value, $abiType)
    {
        $value = Utils::toHex($value);
        $prefix = IntegerFormatter::format(mb_strlen($value) / 2);
        $l = floor((mb_strlen($value) + 63) / 64);
        $padding = (($l * 64 - mb_strlen($value) + 1) >= 0) ? $l * 64 - mb_strlen($value) : 0;

        return $prefix . $value . implode('', array_fill(0, $padding, '0'));
    }

    /**
     * outputFormat
     * 
     * @param mixed $value
     * @param array $abiType
     * @return string
     */
    public function outputFormat($value, $abiType)
    {
        $strLen = mb_substr($value, 0, 64);
        $strValue = mb_substr($value, 64);
        $match = [];

        if (preg_match('/^[0]+([a-f0-9]+)$/', $strLen, $match) === 1) {
            $strLen = BigNumberFormatter::format('0x' . $match[1])->toString();
        }
        if (is_float((int) $strLen * 2)) {
            var_dump($strValue, $strLen, mb_substr($value, 0, 64), BigNumberFormatter::format('0x' . mb_substr($value, 0, 64))->toString());
        }
        $strValue = mb_substr($strValue, 0, (int) $strLen * 2);

        return Utils::hexToBin($strValue);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/Str.php`.

**Classes defined**: Str

**Functions defined**: isType, __construct, outputFormat, isDynamicType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 94
- Code lines: 81
- Comment lines: 39
- Blank lines: -26

### Main Components

**Functions** (5):
- `__construct()`
- `inputFormat()`
- `isDynamicType()`
- `isType()`
- `outputFormat()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/web3.php/src/Contracts/Types/Str.php
```

