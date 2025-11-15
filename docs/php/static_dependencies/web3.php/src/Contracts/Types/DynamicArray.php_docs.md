# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/DynamicArray.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/DynamicArray.php`
- **Size**: 2,187 bytes
- **Lines**: 95
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
use Web3\Utils;
use Web3\Contracts\Types\BaseArray;
use Web3\Formatters\IntegerFormatter;

class DynamicArray extends BaseArray
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
        return (preg_match('/(\[\])/', $name) === 1);
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
        $results = $this->encodeElements($value, $abiType);
        $encodeSize = IntegerFormatter::format(count($value));
        return $encodeSize . implode('', $results);
    }

    /**
     * outputFormat
     * 
     * @param string $value
     * @param array $abiType
     * @return array
     */
    public function outputFormat($value, $abiType)
    {
        if (!is_array($abiType)) {
            throw new InvalidArgumentException('Invalid abiType to decode sized array, expected: array');
        }
        $lengthHex = mb_substr($value, 0, 64);
        $length = (int) Utils::hexToNumber($lengthHex);
        $offset = 0;
        $value = mb_substr($value, 64);
        $results = [];
        $decoder = $abiType['coders'];
        for ($i = 0; $i < $length; $i++) {
            $decodeValueOffset = $offset;
            if ($decoder['dynamic']) {
                $decodeValueOffsetHex = mb_substr($value, $offset, 64);
                $decodeValueOffset = (int) Utils::hexToNumber($decodeValueOffsetHex) * 2;
            }
            $results[] = $decoder['solidityType']->decode($value, $decodeValueOffset, $decoder);
            $offset += 64;
        }
        return $results;
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/DynamicArray.php`.

**Classes defined**: DynamicArray

**Functions defined**: isType, __construct, outputFormat, isDynamicType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 95
- Code lines: 86
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
php php/static_dependencies/web3.php/src/Contracts/Types/DynamicArray.php
```

