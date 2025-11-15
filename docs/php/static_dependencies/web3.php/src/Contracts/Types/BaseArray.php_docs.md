# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/BaseArray.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/BaseArray.php`
- **Size**: 2,628 bytes
- **Lines**: 116
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
use Web3\Contracts\SolidityType;
use Web3\Contracts\Types\IType;
use Web3\Formatters\IntegerFormatter;

class BaseArray extends SolidityType implements IType
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
        return true;
    }

    /**
     * encodeElements
     * 
     * @param mixed $value
     * @param string $name
     * @return array
     */
    public function encodeElements($value, $name)
    {
        if (!is_array($value)) {
            throw new InvalidArgumentException('Encode value must be array');
        }
        $results = [];
        $itemsAreDynamic = false;
        foreach ($value as $key => $val) {
            $results[] = $name['coders']['solidityType']->encode($val, $name['coders']);
            if ($name['coders']['dynamic']) {
                $itemsAreDynamic = true;
            }
        }
        if (!$itemsAreDynamic) {
            return $results;
        }
        $headLength = 32 * count($value);
        $tailOffsets = [0];
        foreach ($results as $key => $val) {
            if ($key === count($results) - 1) {
                break;
            }
            $tailOffsets[] = (int) mb_strlen($val) / 2;
        }
        $headChunks = [];
        $totalOffset = 0;
        foreach ($tailOffsets as $offset) {
            $totalOffset += $offset;
            $headChunks[] = IntegerFormatter::format($headLength + $totalOffset);
        }
        return array_merge($headChunks, $results);
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
        return implode('', $this->encodeElements($value, $abiType));
    }

    /**
     * outputFormat
     * 
     * @param mixed $value
     * @param array $abiType
     * @return string
     */
    // public function outputFormat($value, $abiType)
    // {
    //     throw new InvalidArgumentException('Should not call outputFormat in BaseArray directly');
    // }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/BaseArray.php`.

**Classes defined**: BaseArray

**Functions defined**: isType, __construct, encodeElements, outputFormat, isDynamicType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 116
- Code lines: 102
- Comment lines: 50
- Blank lines: -36

### Main Components

**Functions** (6):
- `__construct()`
- `encodeElements()`
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
php php/static_dependencies/web3.php/src/Contracts/Types/BaseArray.php
```

