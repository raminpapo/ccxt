# Documentation: php/static_dependencies/Sop/ASN1/Type/PrimitiveType.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/PrimitiveType.php`
- **Size**: 274 bytes
- **Lines**: 20
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type;

/**
 * Trait for primitive types.
 */
trait PrimitiveType
{
    /**
     * @see \Sop\ASN1\Feature\ElementBase::isConstructed()
     */
    public function isConstructed(): bool
    {
        return false;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/PrimitiveType.php`.

**Functions defined**: isConstructed

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 16
- Comment lines: 6
- Blank lines: -2

### Main Components

**Functions** (1):
- `isConstructed()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/PrimitiveType.php
```

