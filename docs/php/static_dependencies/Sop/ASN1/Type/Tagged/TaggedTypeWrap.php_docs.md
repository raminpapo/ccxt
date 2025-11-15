# Documentation: php/static_dependencies/Sop/ASN1/Type/Tagged/TaggedTypeWrap.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Tagged/TaggedTypeWrap.php`
- **Size**: 510 bytes
- **Lines**: 36
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Tagged;

use Sop\ASN1\Type\TaggedType;

/**
 * Base class to wrap inner element for tagging.
 */
abstract class TaggedTypeWrap extends TaggedType
{
    /**
     * Wrapped element.
     *
     * @var \Sop\ASN1\Element
     */
    protected $_element;

    /**
     * Type class.
     *
     * @var int
     */
    protected $_class;

    /**
     * {@inheritdoc}
     */
    public function typeClass(): int
    {
        return $this->_class;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Tagged/TaggedTypeWrap.php`.

**Classes defined**: TaggedTypeWrap, to

**Functions defined**: typeClass

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 29
- Comment lines: 16
- Blank lines: -9

### Main Components

**Functions** (1):
- `typeClass()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Tagged/TaggedTypeWrap.php
```

