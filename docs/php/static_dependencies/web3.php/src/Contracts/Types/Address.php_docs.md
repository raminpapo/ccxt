# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/Address.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/Address.php`
- **Size**: 1,610 bytes
- **Lines**: 88
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

use InvalidArgumentException;
use Web3\Contracts\SolidityType;
use Web3\Contracts\Types\IType;
use Web3\Utils;
use Web3\Formatters\IntegerFormatter;

class Address extends SolidityType implements IType
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
        return (preg_match('/^address/', $name) === 1);
    }

    /**
     * isDynamicType
     * 
     * @return bool
     */
    public function isDynamicType()
    {
        return false;
    }

    /**
     * inputFormat
     * to do: iban
     * 
     * @param mixed $value
     * @param array $abiType
     * @return string
     */
    public function inputFormat($value, $abiType)
    {
        $value = (string) $value;

        if (Utils::isAddress($value)) {
            $value = mb_strtolower($value);

            if (Utils::isZeroPrefixed($value)) {
                $value = Utils::stripZero($value);
            }
        }
        $value = IntegerFormatter::format($value);

        return $value;
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
        return '0x' . mb_substr($value, 24, 40);
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/Address.php`.

**Classes defined**: Address

**Functions defined**: isType, __construct, outputFormat, isDynamicType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 88
- Code lines: 76
- Comment lines: 40
- Blank lines: -28

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
php php/static_dependencies/web3.php/src/Contracts/Types/Address.php
```

