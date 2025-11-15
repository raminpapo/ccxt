# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/NumericString.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/NumericString.php`
- **Size**: 610 bytes
- **Lines**: 34
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
 * Implements *NumericString* type.
 */
class NumericString extends PrimitiveString
{
    use UniversalClass;

    /**
     * Constructor.
     */
    public function __construct(string $string)
    {
        $this->_typeTag = self::TYPE_NUMERIC_STRING;
        parent::__construct($string);
    }

    /**
     * {@inheritdoc}
     */
    protected function _validateString(string $string): bool
    {
        return 0 == preg_match('/[^0-9 ]/', $string);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/NumericString.php`.

**Classes defined**: NumericString

**Functions defined**: __construct, _validateString

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 27
- Comment lines: 9
- Blank lines: -2

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
php php/static_dependencies/Sop/ASN1/Type/Primitive/NumericString.php
```

