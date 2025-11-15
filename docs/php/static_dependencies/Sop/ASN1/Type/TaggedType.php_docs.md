# Documentation: php/static_dependencies/Sop/ASN1/Type/TaggedType.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/TaggedType.php`
- **Size**: 2,508 bytes
- **Lines**: 85
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Element;
use Sop\ASN1\Type\Tagged\ExplicitTagging;
use Sop\ASN1\Type\Tagged\ImplicitTagging;

/**
 * Base class for context-specific types.
 */
abstract class TaggedType extends Element
{
    /**
     * Check whether element supports explicit tagging.
     *
     * @param null|int $expectedTag Optional outer tag expectation
     *
     * @throws \UnexpectedValueException If expectation fails
     */
    public function expectExplicit(?int $expectedTag = null): ExplicitTagging
    {
        $el = $this;
        if (!$el instanceof ExplicitTagging) {
            throw new \UnexpectedValueException(
                "Element doesn't implement explicit tagging.");
        }
        if (isset($expectedTag)) {
            $el->expectTagged($expectedTag);
        }
        return $el;
    }

    /**
     * Get the wrapped inner element employing explicit tagging.
     *
     * @param null|int $expectedTag Optional outer tag expectation
     *
     * @throws \UnexpectedValueException If expectation fails
     */
    public function asExplicit(?int $expectedTag = null): UnspecifiedType
    {
        return $this->expectExplicit($expectedTag)->explicit();
    }

    /**
     * Check whether element supports implicit tagging.
     *
     * @param null|int $expectedTag Optional outer tag expectation
     *
     * @throws \UnexpectedValueException If expectation fails
     */
    public function expectImplicit(?int $expectedTag = null): ImplicitTagging
    {
        $el = $this;
        if (!$el instanceof ImplicitTagging) {
            throw new \UnexpectedValueException(
                "Element doesn't implement implicit tagging.");
        }
        if (isset($expectedTag)) {
            $el->expectTagged($expectedTag);
        }
        return $el;
    }

    /**
     * Get the wrapped inner element employing implicit tagging.
     *
     * @param int      $tag           Type tag of the inner element
     * @param null|int $expectedTag   Optional outer tag expectation
     * @param int      $expectedClass Optional inner type class expectation
     *
     * @throws \UnexpectedValueException If expectation fails
     */
    public function asImplicit(int $tag, ?int $expectedTag = null,
        int $expectedClass = Identifier::CLASS_UNIVERSAL): UnspecifiedType
    {
        return $this->expectImplicit($expectedTag)->implicit($tag,
            $expectedClass);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/TaggedType.php`.

**Classes defined**: for, TaggedType, expectation

**Functions defined**: asImplicit, expectImplicit, asExplicit, expectExplicit

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 85
- Code lines: 77
- Comment lines: 33
- Blank lines: -25

### Main Components

**Classes** (1):
- `expectation`

**Functions** (4):
- `asExplicit()`
- `asImplicit()`
- `expectExplicit()`
- `expectImplicit()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/TaggedType.php
```

