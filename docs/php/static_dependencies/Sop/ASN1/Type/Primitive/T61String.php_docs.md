# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/T61String.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/T61String.php`
- **Size**: 689 bytes
- **Lines**: 36
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
 * Implements *T61String* type.
 */
class T61String extends PrimitiveString
{
    use UniversalClass;

    /**
     * Constructor.
     */
    public function __construct(string $string)
    {
        $this->_typeTag = self::TYPE_T61_STRING;
        parent::__construct($string);
    }

    /**
     * {@inheritdoc}
     */
    protected function _validateString(string $string): bool
    {
        // allow everything since there's literally
        // thousands of allowed characters (16 bit composed characters)
        return true;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/T61String.php`.

**Classes defined**: T61String

**Functions defined**: __construct, _validateString

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 27
- Comment lines: 11
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
php php/static_dependencies/Sop/ASN1/Type/Primitive/T61String.php
```

