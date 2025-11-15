# Documentation: php/static_dependencies/starknet.php/src/Crypto/Key.php

## File Metadata

- **Path**: `php/static_dependencies/starknet.php/src/Crypto/Key.php`
- **Size**: 2,707 bytes
- **Lines**: 90
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

use Exception;
use StarkNet\Constants;
use StarkNet\Utils;

class Key {
    /**
     * grindKey
     * Given a cryptographically-secure seed and a limit, deterministically generates a pseudorandom
     * key in the range [0, limit).
     * This is a reference implementation, and cryptographic security is not guaranteed (for example,
     * it may be vulnerable to side-channel attacks); this function is not recommended for use with key
     * generation on mainnet.
     * 
     * @param BigNumber $keySeed
     * @return string
     */
    public static function grindKey ($keySeed)
    {
        $keySeed = Utils::toBn($keySeed);
        $ecOrder = Utils::toBn(Constants::EC_ORDER);
        list(,$maskDivOrder) = Constants::MASK_256()->divide($ecOrder);
        $maxAllowedValue = Constants::MASK_256()->subtract($maskDivOrder);
        for ($i=0; ; $i++) {
            $msg = str_pad($keySeed->toBytes() . Utils::toBn($i)->toBytes(), 33, "\0");
            $key = Utils::toBn('0x' . \hash('sha256', $msg, false));
            if ($key->compare($maxAllowedValue) < 0) {
                list(,$result) = $key->divide($ecOrder);
                return $result->toHex();
            }
            if ($i === 100000) {
                throw new Exception('grindKey is broken: tried 100k vals');
            }
        }
    }

    /**
     * getPublicKey
     * 
     * @param string $privateKey hex encode
     * @param bool $isCompressed
     * @param string $enc
     * @return string
     */
    public static function getPublicKey ($privateKey, $isCompressed = false, $enc = 'hex')
    {
        $privateKey = Utils::stripZeroPrefix($privateKey);
        $ec = Curve::ec();
        $keyPair = $ec->keyFromPrivate(str_pad($privateKey, 64, '0', STR_PAD_LEFT));
        return $keyPair->getPublic($isCompressed, $enc);
    }

     /**
     * getStarkKey
     * 
     * @param string $privateKey
     * @return string
     */
    public static function getStarkKey ($privateKey)
    {
        $publicKey = self::getPublicKey($privateKey, true, '');
        return '0x' . preg_replace('/^0+/', '', $publicKey->getX()->toString(16));
    }

    /**
     * ethSigToPrivate
     * 
     * @param string $sig
     * @return string
     */
    public static function ethSigToPrivate ($sig)
    {
        $sig = Utils::stripZeroPrefix($sig);
        if (strlen($sig) !== 130) {
            throw new Exception('Wrong ethereum signature');
        }
        return self::grindKey(substr($sig, 0, 64));
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/starknet.php/src/Crypto/Key.php`.

**Classes defined**: Key

**Functions defined**: is, getPublicKey, grindKey, getStarkKey, ethSigToPrivate

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 90
- Code lines: 84
- Comment lines: 39
- Blank lines: -33

### Main Components

**Classes** (1):
- `Key`

**Functions** (5):
- `ethSigToPrivate()`
- `getPublicKey()`
- `getStarkKey()`
- `grindKey()`
- `is()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/starknet.php/src/Crypto/Key.php
```

