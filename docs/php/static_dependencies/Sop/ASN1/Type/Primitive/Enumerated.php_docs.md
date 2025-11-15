# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/Enumerated.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/Enumerated.php`
- **Size**: 365 bytes
- **Lines**: 23
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Primitive;

/**
 * Implements *ENUMERATED* type.
 */
class Enumerated extends Integer
{
    /**
     * Constructor.
     *
     * @param int|string $number
     */
    public function __construct($number)
    {
        parent::__construct($number);
        $this->_typeTag = self::TYPE_ENUMERATED;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/Enumerated.php`.

**Classes defined**: Enumerated

**Functions defined**: __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 19
- Comment lines: 8
- Blank lines: -4

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
php php/static_dependencies/Sop/ASN1/Type/Primitive/Enumerated.php
```

