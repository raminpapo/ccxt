# Documentation: php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitlyTaggedType.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitlyTaggedType.php`
- **Size**: 1,249 bytes
- **Lines**: 59
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Tagged;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Element;
use Sop\ASN1\Type\UnspecifiedType;

/**
 * Implements explicit tagging mode.
 *
 * Explicit tagging wraps a type by prepending a tag. Underlying DER encoding
 * is not changed.
 */
class ExplicitlyTaggedType extends TaggedTypeWrap implements ExplicitTagging
{
    /**
     * Constructor.
     *
     * @param int     $tag     Tag number
     * @param Element $element Wrapped element
     * @param int     $class   Type class
     */
    public function __construct(int $tag, Element $element,
        int $class = Identifier::CLASS_CONTEXT_SPECIFIC)
    {
        $this->_typeTag = $tag;
        $this->_element = $element;
        $this->_class = $class;
    }

    /**
     * {@inheritdoc}
     */
    public function isConstructed(): bool
    {
        return true;
    }

    /**
     * {@inheritdoc}
     */
    public function explicit(): UnspecifiedType
    {
        return $this->_element->asUnspecified();
    }

    /**
     * {@inheritdoc}
     */
    protected function _encodedContentDER(): string
    {
        // get the full encoding of the wrapped element
        return $this->_element->toDER();
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitlyTaggedType.php`.

**Classes defined**: ExplicitlyTaggedType, Type

**Functions defined**: _encodedContentDER, isConstructed, __construct, explicit

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 50
- Comment lines: 23
- Blank lines: -14

### Main Components

**Functions** (4):
- `__construct()`
- `_encodedContentDER()`
- `explicit()`
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
php php/static_dependencies/Sop/ASN1/Type/Tagged/ExplicitlyTaggedType.php
```

