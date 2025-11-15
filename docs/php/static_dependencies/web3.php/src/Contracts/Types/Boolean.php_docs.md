# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/Boolean.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/Boolean.php`
- **Size**: 1,513 bytes
- **Lines**: 81
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

class Boolean extends SolidityType implements IType
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
        return (preg_match('/^bool/', $name) === 1);
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
        if (!is_bool($value)) {
            throw new InvalidArgumentException('The value to inputFormat function must be boolean.');
        }
        $value = (int) $value;

        return '000000000000000000000000000000000000000000000000000000000000000' . $value;
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
        $value = (int) mb_substr($value, 63, 1);

        return (bool) $value;
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/Boolean.php`.

**Classes defined**: Boolean

**Functions defined**: isType, must, __construct, outputFormat, isDynamicType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 70
- Comment lines: 39
- Blank lines: -28

### Main Components

**Functions** (6):
- `__construct()`
- `inputFormat()`
- `isDynamicType()`
- `isType()`
- `must()`
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
php php/static_dependencies/web3.php/src/Contracts/Types/Boolean.php
```

