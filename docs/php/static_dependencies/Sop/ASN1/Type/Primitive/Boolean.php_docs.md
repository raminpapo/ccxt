# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/Boolean.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/Boolean.php`
- **Size**: 1,473 bytes
- **Lines**: 74
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Primitive;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Component\Length;
use Sop\ASN1\Element;
use Sop\ASN1\Exception\DecodeException;
use Sop\ASN1\Feature\ElementBase;
use Sop\ASN1\Type\PrimitiveType;
use Sop\ASN1\Type\UniversalClass;

/**
 * Implements *BOOLEAN* type.
 */
class Boolean extends Element
{
    use UniversalClass;
    use PrimitiveType;

    /**
     * Value.
     *
     * @var bool
     */
    private $_bool;

    /**
     * Constructor.
     */
    public function __construct(bool $bool)
    {
        $this->_typeTag = self::TYPE_BOOLEAN;
        $this->_bool = $bool;
    }

    /**
     * Get the value.
     */
    public function value(): bool
    {
        return $this->_bool;
    }

    /**
     * {@inheritdoc}
     */
    protected function _encodedContentDER(): string
    {
        return $this->_bool ? chr(0xff) : chr(0);
    }

    /**
     * {@inheritdoc}
     */
    protected static function _decodeFromDER(Identifier $identifier,
        string $data, int &$offset): ElementBase
    {
        $idx = $offset;
        Length::expectFromDER($data, $idx, 1);
        $byte = ord($data[$idx++]);
        if (0 !== $byte) {
            if (0xff !== $byte) {
                throw new DecodeException(
                    'DER encoded boolean true must have all bits set to 1.');
            }
        }
        $offset = $idx;
        return new self(0 !== $byte);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/Boolean.php`.

**Classes defined**: Boolean

**Functions defined**: value, _encodedContentDER, _decodeFromDER, __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 74
- Code lines: 64
- Comment lines: 20
- Blank lines: -10

### Main Components

**Functions** (4):
- `__construct()`
- `_decodeFromDER()`
- `_encodedContentDER()`
- `value()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Primitive/Boolean.php
```

