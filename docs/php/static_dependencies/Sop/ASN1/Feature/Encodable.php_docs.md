# Documentation: php/static_dependencies/Sop/ASN1/Feature/Encodable.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Feature/Encodable.php`
- **Size**: 231 bytes
- **Lines**: 17
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Feature;

/**
 * Interface for classes that may be encoded to DER.
 */
interface Encodable
{
    /**
     * Encode object to DER.
     */
    public function toDER(): string;
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Feature/Encodable.php`.

**Functions defined**: toDER

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 13
- Comment lines: 6
- Blank lines: -2

### Main Components

**Functions** (1):
- `toDER()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Feature/Encodable.php
```

