# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/SizedArray.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/SizedArray.php`
- **Size**: 2,632 bytes
- **Lines**: 103
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

class SizedArray extends BaseArray
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
        return (preg_match('/(\[([0-9]*)\])/', $name) === 1);
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
        if (!is_array($value)) {
            throw new InvalidArgumentException('Encode value must be array');
        }
        $length = is_array($abiType) ? $this->staticArrayLength($abiType['type']) : 0;
        if ($length === 0 || count($value) > $length) {
            throw new InvalidArgumentException('Invalid value to encode sized array, expected: ' . $length . ', but got ' . count($value));
        }
        return parent::inputFormat($value, $abiType);
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
        $length = is_array($abiType) ? $this->staticArrayLength($abiType['type']) : 0;
        $offset = 0;
        $results = [];
        $decoder = $abiType['coders'];
        for ($i = 0; $i < $length; $i++) {
            $decodeValueOffset = $offset;
            if ($decoder['dynamic']) {
                $decodeValueOffsetHex = mb_substr($value, $offset, 64);
                $decodeValueOffset = (int) Utils::hexToNumber($decodeValueOffsetHex) * 2;
            }
            $decoded = $decoder['solidityType']->decode($value, $decodeValueOffset, $decoder);
            $results[] = $decoded;
            $dataCount = 1;
            if (!$decoder['dynamic']) {
                $dataCount = $this->deepCalculateDataLength($decoded);
            }
            $offset += (64 * $dataCount);
        }
        return $results;
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/SizedArray.php`.

**Classes defined**: SizedArray

**Functions defined**: isType, __construct, outputFormat, isDynamicType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 103
- Code lines: 94
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
php php/static_dependencies/web3.php/src/Contracts/Types/SizedArray.php
```

