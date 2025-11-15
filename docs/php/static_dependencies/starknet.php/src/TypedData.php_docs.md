# Documentation: php/static_dependencies/starknet.php/src/TypedData.php

## File Metadata

- **Path**: `php/static_dependencies/starknet.php/src/TypedData.php`
- **Size**: 5,755 bytes
- **Lines**: 206
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
use StarkNet\Cairo\Felt;
use StarkNet\Hash;
use InvalidArgumentException;

/**
 * TypedData
 * Encod typed data for revision 0.
 * 
 * TODO: implement revision 1
 */
class TypedData
{
    /**
     * findType
     * 
     * @param string $type
     * @param array $types
     * @return string
     */
    protected static function findType(string $type, array $types)
    {
        $result = [];
        if ($type === 'felt') {
            return $result;
        } else if (!array_key_exists($type, $types)) {
            throw new InvalidArgumentException('No definition of type ' . $type);
        }

        $result[] = $type;
        foreach ($types[$type] as $field) {
            $subResult = self::findType($field['type'], $types);
            if (count($subResult) > 0) {
                foreach ($subResult as $subType) {
                    if (!in_array($subType, $result)) {
                        $result[] = $subType;
                    }
                }
            }
        }
        return $result;
    }

    /**
     * hashType
     * 
     * @param string $type
     * @param array $types
     * @return string
     */
    public static function hashType($type, $types)
    {
        $result = '';
        $unsortedDeps = self::findType($type, $types);
        if (in_array($type, $unsortedDeps)) {
            array_splice($unsortedDeps, array_search($type, $unsortedDeps), 1);
        }
        sort($unsortedDeps);
        $deps = array_merge([ $type ], $unsortedDeps);
        foreach ($deps as $type) {
            $params = [];
            foreach ($types[$type] as $param) {
                $params[] = $param['name'] . ':' . $param['type'];
            }
            $result .= $type . '(' . implode(',', $params) . ')';
        }
        return '0x' . Hash::getSelectorFromName($result);
    }

    /**
     * encodeField
     * 
     * @param array $types
     * @param string $type
     * @param mixed $value
     * @return string
     */
    protected static function encodeField($types, $type, $value)
    {
        if (substr($type, 0, 1) === '*') {
            // pointer
            $type = substr($type, 1);
            if (array_key_exists($type, $types)) {
                // struct
                $result = [];
                foreach ($value as $data) {
                    $result[] = self::hashStruct($type, $types, $data);
                }
                return '0x' . Utils::removeLeadingZero(FastPedersenHash::computeHashOnElements($result)->toString(16));
            }
        }
        if (array_key_exists($type, $types)) {
            // struct
            return self::hashStruct($type, $types, $value);
        }
        return Utils::toHex($value, true);
    }

    /**
     * encodeData
     * 
     * @param string $type
     * @param array $types
     * @param array $data
     * @return string
     */
    public static function encodeData(string $type, array $types, array $data)
    {
        $encodedValues = [];
        foreach ($types[$type] as $field) {
            $value = self::encodeField($types, $field['type'], $data[$field['name']]);
            $encodedValues[] = $value;
        }

        return $encodedValues;
    }

    /**
     * hashStruct
     * 
     * @param string $typeName
     * @param array $messageTypes
     * @param array $message
     * @return string
     */
    public static function hashStruct($typeName, $messageTypes, $message)
    {
        return '0x' . Utils::removeLeadingZero(FastPedersenHash::computeHashOnElements(array_merge([
            self::hashType($typeName, $messageTypes)
        ], self::encodeData($typeName, $messageTypes, $message)))->toString(16));
    }

    /**
     * hashDomain
     * 
     * @param array $data
     * @return string
     */
    public static function hashDomain($domainData)
    {
        $revision0Domain = [
            'name' => [
                'name' => 'name',
                'type' => 'felt'
            ],
            'chainId' => [
                'name' => 'chainId',
                'type' => 'felt'
            ],
            'version' => [
                'name' => 'version',
                'type' => 'felt'
            ]
        ];
        foreach ($domainData as $key => $data) {
            if (!array_key_exists($key, $revision0Domain)) {
                throw new InvalidArgumentException('Invalid domain key: ' . $key);
            }
        }
        $domainTypes = [
            'StarkNetDomain' => []
        ];
        foreach ($revision0Domain as $key => $data) {
            if (array_key_exists($key, $domainData)) {
                $domainTypes['StarkNetDomain'][] = $revision0Domain[$key];
            }
        }
        return self::hashStruct('StarkNetDomain', $domainTypes, $domainData);
    }

    /**
     * messageHash
     * 
     * @param array $domain
     * @param array $messageTypes
     * @param array $messageData
     * @param string $address
     * @return string
     */
    public static function messageHash($domain, $messageTypes, $messageData, $address)
    {
        $types = array_keys($messageTypes);
        $primaryType = $types[0];
        $message = [
            '0x' . Felt::encodeShortString("StarkNet Message"),
            self::hashDomain($domain),
            $address,
            self::hashStruct($primaryType, $messageTypes, $messageData)
        ];
        return '0x' . Utils::removeLeadingZero(FastPedersenHash::computeHashOnElements($message)->toString(16));
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/starknet.php/src/TypedData.php`.

**Classes defined**: TypedData

**Functions defined**: hashType, hashStruct, encodeData, encodeField, messageHash, findType, hashDomain

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 206
- Code lines: 192
- Comment lines: 70
- Blank lines: -56

### Main Components

**Classes** (1):
- `TypedData`

**Functions** (7):
- `encodeData()`
- `encodeField()`
- `findType()`
- `hashDomain()`
- `hashStruct()`
- `hashType()`
- `messageHash()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/starknet.php/src/TypedData.php
```

