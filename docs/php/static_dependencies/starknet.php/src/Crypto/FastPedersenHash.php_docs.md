# Documentation: php/static_dependencies/starknet.php/src/Crypto/FastPedersenHash.php

## File Metadata

- **Path**: `php/static_dependencies/starknet.php/src/Crypto/FastPedersenHash.php`
- **Size**: 1,925 bytes
- **Lines**: 72
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

class FastPedersenHash
{
    use Hash;
    
    // 2 ** 248 - 1
    public static function LOW_BITS_MASK()
    {
        return Utils::toBn('452312848583266388373324160190187140051835877600158453279131187530910662655');
    }

    /**
     * processSingleElement
     * 
     * @param BigNumber $element
     * @param Point $x
     * @param Point $y
     * @return Point
     */
    private static function processSingleElement($element, $p1, $p2)
    {
        $cmpZero = $element->compare(Constants::ZERO());
        assert($cmpZero >= 0 && $element->compare(Utils::toBn('0x' . Constants::FIELD_PRIME)) < 0, "Element value is out of range");
        $highNibble = $element->bitwise_rightShift(Constants::LOW_PART_BITS)->toHex();
        $lowPart = $element->bitwise_and(self::LOW_BITS_MASK())->toHex();
        if ($highNibble === '') {
            $highNibble = '0';
        }
        if ($lowPart === '') {
            $lowPart = '0';
        }
        return $p1->mul($lowPart)->add($p2->mul($highNibble));
    }

    /**
     * hash
     * pedersen hash
     * 
     * @param mixed $x
     * @param mixed $y
     * @return BigNumber pedersen hash of x and y
     */
    public static function hash($x, $y)
    {
        $xBn = Utils::toBn($x);
        $yBn = Utils::toBn($y);
        $points = Curve::constantPointsPedersen();
        $hashShiftPoint = $points[0];
        $p0 = $points[1];
        $p1 = $points[2];
        $p2 = $points[3];
        $p3 = $points[4];
        return ($hashShiftPoint->add(self::processSingleElement($xBn, $p0, $p1))->add(self::processSingleElement($yBn, $p2, $p3)))->getX();
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/starknet.php/src/Crypto/FastPedersenHash.php`.

**Classes defined**: FastPedersenHash

**Functions defined**: hash, processSingleElement, LOW_BITS_MASK

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 64
- Comment lines: 25
- Blank lines: -17

### Main Components

**Classes** (1):
- `FastPedersenHash`

**Functions** (3):
- `LOW_BITS_MASK()`
- `hash()`
- `processSingleElement()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/starknet.php/src/Crypto/FastPedersenHash.php
```

