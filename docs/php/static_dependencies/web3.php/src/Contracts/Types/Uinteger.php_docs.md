# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/Uinteger.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/Uinteger.php`
- **Size**: 1,371 bytes
- **Lines**: 76
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

class Uinteger extends SolidityType implements IType
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
        return (preg_match('/^uint([0-9]{1,})?/', $name) === 1);
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
     * 
     * @param mixed $value
     * @param array $abiType
     * @return string
     */
    public function inputFormat($value, $abiType)
    {
        return IntegerFormatter::format($value);
    }

    /**
     * outputFormat
     * 
     * @param mixed $value
     * @param array $abiType
     * @return BigNumber
     */
    public function outputFormat($value, $abiType)
    {
        return BigNumberFormatter::format('0x' . mb_substr($value, 0, 64));
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/Uinteger.php`.

**Classes defined**: Uinteger

**Functions defined**: isType, __construct, outputFormat, isDynamicType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 67
- Comment lines: 39
- Blank lines: -30

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
php php/static_dependencies/web3.php/src/Contracts/Types/Uinteger.php
```

