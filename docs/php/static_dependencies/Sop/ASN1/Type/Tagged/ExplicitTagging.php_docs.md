# Documentation: php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitTagging.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitTagging.php`
- **Size**: 360 bytes
- **Lines**: 20
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Tagged;

use Sop\ASN1\Feature\ElementBase;
use Sop\ASN1\Type\UnspecifiedType;

/**
 * Interface for classes providing explicit tagging.
 */
interface ExplicitTagging extends ElementBase
{
    /**
     * Get explicitly tagged wrapped element.
     */
    public function explicit(): UnspecifiedType;
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitTagging.php`.

**Functions defined**: explicit

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 15
- Comment lines: 6
- Blank lines: -1

### Main Components

**Functions** (1):
- `explicit()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitTagging.php
```

