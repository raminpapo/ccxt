# Documentation: php/static_dependencies/starknet.php/src/Hash.php

## File Metadata

- **Path**: `php/static_dependencies/starknet.php/src/Hash.php`
- **Size**: 1,544 bytes
- **Lines**: 59
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

namespace StarkNet;

use BN\BN;
use StarkNet\Utils;
use StarkNet\Crypto\FastPedersenHash;

class Hash
{
    const CONTRACT_ADDRESS_PREFIX = '523065374597054866729014270389667305596563390979550329787219';

    public static function L2_ADDRESS_UPPER_BOUND()
    {
        // 2**251 - 256
        return new BN('3618502788666131106986593281521497120414687020801267626233049500247285300992');
    }

    /**
     * getSelectorFromName
     * 
     * @param string $name
     * @return string
     */
    public static function getSelectorFromName($name)
    {
        return Utils::removeLeadingZero(Utils::keccak($name));
    }

    /**
     * computeAddress
     * 
     * @param mixed $classHash
     * @param mixed $constructorData
     * @param mixed $salt
     * @param mixed $deployerAddress
     * @return string
     */
    public static function computeAddress($classHash, $constructorData, $salt, $deployerAddress = 0)
    {
        $constructorDataHash = FastPedersenHash::computeHashOnElements($constructorData);
        $rawAddress =  FastPedersenHash::computeHashOnElements([
            self::CONTRACT_ADDRESS_PREFIX,
            $deployerAddress,
            $salt,
            $classHash,
            $constructorDataHash
        ]);
        return '0x' . Utils::removeLeadingZero($rawAddress->mod(self::L2_ADDRESS_UPPER_BOUND())->toString(16));
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/starknet.php/src/Hash.php`.

**Classes defined**: Hash

**Functions defined**: getSelectorFromName, L2_ADDRESS_UPPER_BOUND, computeAddress

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 52
- Comment lines: 24
- Blank lines: -17

### Main Components

**Classes** (1):
- `Hash`

**Functions** (3):
- `L2_ADDRESS_UPPER_BOUND()`
- `computeAddress()`
- `getSelectorFromName()`

**Constants** (1):
- `CONTRACT_ADDRESS_PREFIX`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/starknet.php/src/Hash.php
```

