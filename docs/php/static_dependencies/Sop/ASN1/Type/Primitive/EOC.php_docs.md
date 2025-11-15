# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/EOC.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/EOC.php`
- **Size**: 1,127 bytes
- **Lines**: 55
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
 * Implements *End-of-contents* type.
 */
class EOC extends Element
{
    use UniversalClass;
    use PrimitiveType;

    /**
     * Constructor.
     */
    public function __construct()
    {
        $this->_typeTag = self::TYPE_EOC;
    }

    /**
     * {@inheritdoc}
     */
    protected function _encodedContentDER(): string
    {
        return '';
    }

    /**
     * {@inheritdoc}
     */
    protected static function _decodeFromDER(Identifier $identifier,
        string $data, int &$offset): ElementBase
    {
        $idx = $offset;
        if (!$identifier->isPrimitive()) {
            throw new DecodeException('EOC value must be primitive.');
        }
        // EOC type has always zero length
        Length::expectFromDER($data, $idx, 0);
        $offset = $idx;
        return new self();
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/EOC.php`.

**Classes defined**: EOC

**Functions defined**: _encodedContentDER, _decodeFromDER, __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 46
- Comment lines: 13
- Blank lines: -4

### Main Components

**Functions** (3):
- `__construct()`
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
php php/static_dependencies/Sop/ASN1/Type/Primitive/EOC.php
```

