# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/CharacterString.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/CharacterString.php`
- **Size**: 452 bytes
- **Lines**: 26
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
 * Implements *CHARACTER STRING* type.
 */
class CharacterString extends PrimitiveString
{
    use UniversalClass;

    /**
     * Constructor.
     */
    public function __construct(string $string)
    {
        $this->_typeTag = self::TYPE_CHARACTER_STRING;
        parent::__construct($string);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/CharacterString.php`.

**Classes defined**: CharacterString

**Functions defined**: __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 20
- Comment lines: 6
- Blank lines: 0

### Main Components

**Functions** (1):
- `__construct()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Primitive/CharacterString.php
```

