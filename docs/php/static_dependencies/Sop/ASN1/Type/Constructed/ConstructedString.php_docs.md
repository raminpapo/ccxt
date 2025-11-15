# Documentation: php/static_dependencies/Sop/ASN1/Type/Constructed/ConstructedString.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Constructed/ConstructedString.php`
- **Size**: 3,506 bytes
- **Lines**: 132
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Constructed;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Element;
use Sop\ASN1\Feature\ElementBase;
use Sop\ASN1\Type\StringType;
use Sop\ASN1\Type\Structure;

/**
 * Implements constructed type of simple strings.
 *
 * Constructed strings only exist in BER encodings, and often with
 * indefinite length. Generally constructed string must contain only elements
 * that have the same type tag as the constructing element.
 * For example:
 * ```
 *  OCTET STRING (cons) {
 *      OCTET STRING (prim) "ABC"
 *      OCTET STRING (prim) "DEF"
 *  }
 * ```
 * Canonically this corresponds to a payload of "ABCDEF" string.
 *
 * From API standpoint this can also be seen as a string type
 * (as it implements `StringType`), and thus `UnspecifiedType::asString()`
 * method may return `ConstructedString` instances.
 */
class ConstructedString extends Structure implements StringType
{
    /**
     * Constructor.
     *
     * @internal Use `create()` or `createWithTag()` method instead
     *
     * @param Element ...$elements Any number of elements
     */
    protected function __construct(Element ...$elements)
    {
        parent::__construct(...$elements);
    }

    /**
     * {@inheritdoc}
     */
    public function __toString(): string
    {
        return $this->string();
    }

    /**
     * Create from a list of string type elements.
     *
     * All strings must have the same type.
     *
     * @param StringType ...$elements
     *
     * @throws \LogicException
     */
    public static function create(StringType ...$elements): self
    {
        if (!count($elements)) {
            throw new \LogicException('No elements, unable to determine type tag.');
        }
        $tag = $elements[0]->tag();
        foreach ($elements as $el) {
            if ($el->tag() !== $tag) {
                throw new \LogicException(
                    'All elements in constructed string must have the same type.');
            }
        }
        return self::createWithTag($tag, ...$elements);
    }

    /**
     * Create from strings with a given type tag.
     *
     * Does not perform any validation on types.
     *
     * @param int        $tag         Type tag for the constructed string element
     * @param StringType ...$elements Any number of elements
     *
     * @return self
     */
    public static function createWithTag(int $tag, StringType ...$elements)
    {
        $el = new self(...$elements);
        $el->_typeTag = $tag;
        return $el;
    }

    /**
     * Get a list of strings in this structure.
     *
     * @return string[]
     */
    public function strings(): array
    {
        return array_map(function (StringType $el) {
            return $el->string();
        }, $this->_elements);
    }

    /**
     * Get the contained strings concatenated together.
     *
     * NOTE: It's unclear how bit strings with unused bits should be concatenated.
     */
    public function string(): string
    {
        return implode('', $this->strings());
    }

    /**
     * {@inheritdoc}
     *
     * @return self
     */
    protected static function _decodeFromDER(Identifier $identifier,
        string $data, int &$offset): ElementBase
    {
        /** @var ConstructedString $type */
        $type = forward_static_call_array([parent::class, __FUNCTION__],
            [$identifier, $data, &$offset]);
        $type->_typeTag = $identifier->intTag();
        return $type;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Constructed/ConstructedString.php`.

**Classes defined**: ConstructedString

**Functions defined**: strings, string, __toString, _decodeFromDER, __construct, create, createWithTag

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 132
- Code lines: 121
- Comment lines: 64
- Blank lines: -53

### Main Components

**Functions** (7):
- `__construct()`
- `__toString()`
- `_decodeFromDER()`
- `create()`
- `createWithTag()`
- `string()`
- `strings()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Constructed/ConstructedString.php
```

