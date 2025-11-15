# Documentation: php/static_dependencies/Sop/ASN1/Type/Constructed/Set.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Constructed/Set.php`
- **Size**: 1,490 bytes
- **Lines**: 64
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Constructed;

use Sop\ASN1\Element;
use Sop\ASN1\Type\Structure;

/**
 * Implements *SET* and *SET OF* types.
 */
class Set extends Structure
{
    /**
     * Constructor.
     *
     * @param Element ...$elements Any number of elements
     */
    public function __construct(Element ...$elements)
    {
        $this->_typeTag = self::TYPE_SET;
        parent::__construct(...$elements);
    }

    /**
     * Sort by canonical ascending order.
     *
     * Used for DER encoding of *SET* type.
     */
    public function sortedSet(): self
    {
        $obj = clone $this;
        usort($obj->_elements,
            function (Element $a, Element $b) {
                if ($a->typeClass() !== $b->typeClass()) {
                    return $a->typeClass() < $b->typeClass() ? -1 : 1;
                }
                if ($a->tag() === $b->tag()) {
                    return 0;
                }
                return $a->tag() < $b->tag() ? -1 : 1;
            });
        return $obj;
    }

    /**
     * Sort by encoding ascending order.
     *
     * Used for DER encoding of *SET OF* type.
     */
    public function sortedSetOf(): self
    {
        $obj = clone $this;
        usort($obj->_elements,
            function (Element $a, Element $b) {
                $a_der = $a->toDER();
                $b_der = $b->toDER();
                return strcmp($a_der, $b_der);
            });
        return $obj;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Constructed/Set.php`.

**Classes defined**: Set

**Functions defined**: __construct, sortedSetOf, sortedSet

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 57
- Comment lines: 18
- Blank lines: -11

### Main Components

**Functions** (3):
- `__construct()`
- `sortedSet()`
- `sortedSetOf()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Constructed/Set.php
```

