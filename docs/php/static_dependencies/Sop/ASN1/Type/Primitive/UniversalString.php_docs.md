# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/UniversalString.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/UniversalString.php`
- **Size**: 779 bytes
- **Lines**: 40
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Primitive;

use Sop\ASN1\Type\PrimitiveString;
use Sop\ASN1\Type\UniversalClass;

/**
 * Implements *UniversalString* type.
 *
 * Universal string is an Unicode string with UCS-4 encoding.
 */
class UniversalString extends PrimitiveString
{
    use UniversalClass;

    /**
     * Constructor.
     */
    public function __construct(string $string)
    {
        $this->_typeTag = self::TYPE_UNIVERSAL_STRING;
        parent::__construct($string);
    }

    /**
     * {@inheritdoc}
     */
    protected function _validateString(string $string): bool
    {
        // UCS-4 has fixed with of 4 octets (32 bits)
        if (0 !== strlen($string) % 4) {
            return false;
        }
        return true;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/UniversalString.php`.

**Classes defined**: UniversalString

**Functions defined**: __construct, _validateString

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 32
- Comment lines: 12
- Blank lines: -4

### Main Components

**Functions** (2):
- `__construct()`
- `_validateString()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Primitive/UniversalString.php
```

