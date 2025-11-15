# Documentation: php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitlyTaggedType.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitlyTaggedType.php`
- **Size**: 1,813 bytes
- **Lines**: 69
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
 * Implements implicit tagging mode.
 *
 * Implicit tagging changes the tag of the tagged type. This changes the
 * DER encoding of the type, and hence the abstract syntax must be known when
 * decoding the data.
 */
class ImplicitlyTaggedType extends TaggedTypeWrap implements ImplicitTagging
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
        // depends on the underlying type
        return $this->_element->isConstructed();
    }

    /**
     * {@inheritdoc}
     */
    public function implicit(
        int $tag, int $class = Identifier::CLASS_UNIVERSAL): UnspecifiedType
    {
        $this->_element->expectType($tag);
        if ($this->_element->typeClass() !== $class) {
            throw new \UnexpectedValueException(
                sprintf('Type class %s expected, got %s.',
                    Identifier::classToName($class),
                    Identifier::classToName($this->_element->typeClass())));
        }
        return $this->_element->asUnspecified();
    }

    /**
     * {@inheritdoc}
     */
    protected function _encodedContentDER(): string
    {
        // get only the content of the wrapped element.
        return $this->_element->_encodedContentDER();
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitlyTaggedType.php`.

**Classes defined**: Type, ImplicitlyTaggedType

**Functions defined**: _encodedContentDER, implicit, isConstructed, __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 69
- Code lines: 59
- Comment lines: 25
- Blank lines: -15

### Main Components

**Functions** (4):
- `__construct()`
- `_encodedContentDER()`
- `implicit()`
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
php php/static_dependencies/Sop/ASN1/Type/Tagged/ImplicitlyTaggedType.php
```

