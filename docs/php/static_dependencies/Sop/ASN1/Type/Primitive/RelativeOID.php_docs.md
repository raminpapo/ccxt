# Documentation: php/static_dependencies/Sop/ASN1/Type/Primitive/RelativeOID.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/Type/Primitive/RelativeOID.php`
- **Size**: 1,113 bytes
- **Lines**: 49
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1\Type\Primitive;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Component\Length;
use Sop\ASN1\Feature\ElementBase;

/**
 * Implements *RELATIVE-OID* type.
 */
class RelativeOID extends ObjectIdentifier
{
    /**
     * Constructor.
     *
     * @param string $oid OID in dotted format
     */
    public function __construct(string $oid)
    {
        $this->_oid = $oid;
        $this->_subids = self::_explodeDottedOID($oid);
        $this->_typeTag = self::TYPE_RELATIVE_OID;
    }

    /**
     * {@inheritdoc}
     */
    protected function _encodedContentDER(): string
    {
        return self::_encodeSubIDs(...$this->_subids);
    }

    /**
     * {@inheritdoc}
     */
    protected static function _decodeFromDER(Identifier $identifier,
        string $data, int &$offset): ElementBase
    {
        $idx = $offset;
        $len = Length::expectFromDER($data, $idx)->intLength();
        $subids = self::_decodeSubIDs(substr($data, $idx, $len));
        $offset = $idx + $len;
        return new self(self::_implodeSubIDs(...$subids));
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/Type/Primitive/RelativeOID.php`.

**Classes defined**: RelativeOID

**Functions defined**: _encodedContentDER, _decodeFromDER, __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 42
- Comment lines: 14
- Blank lines: -7

### Main Components

**Functions** (3):
- `__construct()`
- `_decodeFromDER()`
- `_encodedContentDER()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/Sop/ASN1/Type/Primitive/RelativeOID.php
```

