# Documentation: php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitTagging.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitTagging.php`
- **Size**: 625 bytes
- **Lines**: 26
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Tagged;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Feature\ElementBase;
use Sop\ASN1\Type\UnspecifiedType;

/**
 * Interface for classes providing implicit tagging.
 */
interface ImplicitTagging extends ElementBase
{
    /**
     * Get implicitly tagged wrapped element.
     *
     * @param int $tag   Tag of the element
     * @param int $class Expected type class of the element
     *
     * @throws \UnexpectedValueException If expectation fails
     */
    public function implicit(int $tag, int $class = Identifier::CLASS_UNIVERSAL): UnspecifiedType;
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitTagging.php`.

**Classes defined**: Expected, of

**Functions defined**: implicit

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 21
- Comment lines: 11
- Blank lines: -6

### Main Components

**Functions** (1):
- `implicit()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitTagging.php
```

