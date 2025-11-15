# Documentation: php/static_dependencies/Sop/ASN1/Type/PrimitiveString.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/PrimitiveString.php`
- **Size**: 1,389 bytes
- **Lines**: 54
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Component\Length;
use Sop\ASN1\Exception\DecodeException;
use Sop\ASN1\Feature\ElementBase;

/**
 * Base class for primitive strings.
 *
 * Used by types that don't require special processing of the encoded string data.
 *
 * @internal
 */
abstract class PrimitiveString extends BaseString
{
    use PrimitiveType;

    /**
     * {@inheritdoc}
     */
    protected function _encodedContentDER(): string
    {
        return $this->_string;
    }

    /**
     * {@inheritdoc}
     */
    protected static function _decodeFromDER(Identifier $identifier,
        string $data, int &$offset): ElementBase
    {
        $idx = $offset;
        if (!$identifier->isPrimitive()) {
            throw new DecodeException('DER encoded string must be primitive.');
        }
        $length = Length::expectFromDER($data, $idx)->intLength();
        $str = $length ? substr($data, $idx, $length) : '';
        // substr should never return false, since length is
        // checked by Length::expectFromDER.
        assert(is_string($str), new DecodeException('substr'));
        $offset = $idx + $length;
        try {
            return new static($str);
        } catch (\InvalidArgumentException $e) {
            throw new DecodeException($e->getMessage(), 0, $e);
        }
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/PrimitiveString.php`.

**Classes defined**: for, PrimitiveString

**Functions defined**: _encodedContentDER, _decodeFromDER

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 45
- Comment lines: 15
- Blank lines: -6

### Main Components

**Functions** (2):
- `_decodeFromDER()`
- `_encodedContentDER()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/PrimitiveString.php
```

