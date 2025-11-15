# Documentation: php/static_dependencies/starknet.php/src/Crypto/PedersenHash.php

## File Metadata

- **Path**: `php/static_dependencies/starknet.php/src/Crypto/PedersenHash.php`
- **Size**: 1,594 bytes
- **Lines**: 57
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

namespace StarkNet\Crypto;

use StarkNet\Constants;
use StarkNet\Utils;
use StarkNet\Crypto\Curve;
use StarkNet\Crypto\Hash;

class PedersenHash
{
    use Hash;
    
    /**
     * hash
     * pedersen hash
     * 
     * @param mixed $x
     * @param mixed $y
     * @return BigNumber pedersen hash of the elements
     */
    public static function hash($x, $y)
    {
        return self::pedersenHashAsPoint([$x, $y]);
    }

    private static function pedersenHashAsPoint($elements)
    {
        $points = Curve::constantPoints();
        $point = $points[0];
        foreach ($elements as $i => $ox) {
            $x = Utils::toBN($ox);
            $cmpZero = $x->compare(Constants::ZERO());
            assert($cmpZero >= 0 && $x->compare(Utils::toBN('0x' . Constants::FIELD_PRIME)) < 0, "Invalid input $x");
            $pointList = array_slice($points, 2 + $i * Constants::N_ELEMENT_BITS_HASH, Constants::N_ELEMENT_BITS_HASH);
            assert(count($pointList) == Constants::N_ELEMENT_BITS_HASH, 'invalid point list');
            foreach ($pointList as $pt) {
                assert(!$point->getX()->eq($pt->getX()));
                $val = (int) $x->bitwise_and(Constants::ONE())->toString();
                if ($val !== 0) {
                    $point = $point->add($pt);
                }
                $x = $x->bitwise_rightShift(1);
            }
        }
        return $point->getX();
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/starknet.php/src/Crypto/PedersenHash.php`.

**Classes defined**: PedersenHash

**Functions defined**: hash, pedersenHashAsPoint

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 51
- Comment lines: 16
- Blank lines: -10

### Main Components

**Classes** (1):
- `PedersenHash`

**Functions** (2):
- `hash()`
- `pedersenHashAsPoint()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/starknet.php/src/Crypto/PedersenHash.php
```

