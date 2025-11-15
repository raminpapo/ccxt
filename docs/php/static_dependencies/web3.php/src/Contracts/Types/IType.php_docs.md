# Documentation: php/static_dependencies/web3.php/src/Contracts/Types/IType.php

## File Metadata

- **Path**: `php/static_dependencies/web3.php/src/Contracts/Types/IType.php`
- **Size**: 621 bytes
- **Lines**: 39
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

interface IType
{
    /**
     * isType
     * 
     * @param string $name
     * @return bool
     */
    public function isType($name);

    /**
     * isDynamicType
     * 
     * @return bool
     */
    public function isDynamicType();

    /**
     * inputFormat
     * 
     * @param mixed $value
     * @param array $abiType
     * @return string
     */
    public function inputFormat($value, $abiType);
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/web3.php/src/Contracts/Types/IType.php`.

**Functions defined**: isDynamicType, isType, inputFormat

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 34
- Comment lines: 26
- Blank lines: -21

### Main Components

**Functions** (3):
- `inputFormat()`
- `isDynamicType()`
- `isType()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/web3.php/src/Contracts/Types/IType.php
```

