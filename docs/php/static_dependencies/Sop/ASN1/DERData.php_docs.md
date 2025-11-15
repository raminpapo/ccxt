# Documentation: php/static_dependencies/Sop/ASN1/DERData.php

## File Metadata

- **Path**: `php/static_dependencies/Sop/ASN1/DERData.php`
- **Size**: 1,784 bytes
- **Lines**: 90
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

declare(strict_types = 1);

namespace Sop\ASN1;

use Sop\ASN1\Component\Identifier;
use Sop\ASN1\Component\Length;

/**
 * Container for raw DER encoded data.
 *
 * May be inserted into structure without decoding first.
 */
class DERData extends Element
{
    /**
     * DER encoded data.
     *
     * @var string
     */
    protected $_der;

    /**
     * Identifier of the underlying type.
     *
     * @var Identifier
     */
    protected $_identifier;

    /**
     * Offset to the content in DER data.
     *
     * @var int
     */
    protected $_contentOffset = 0;

    /**
     * Constructor.
     *
     * @param string $data DER encoded data
     *
     * @throws \Sop\ASN1\Exception\DecodeException If data does not adhere to DER
     */
    public function __construct(string $data)
    {
        $this->_identifier = Identifier::fromDER($data, $this->_contentOffset);
        // check that length encoding is valid
        Length::expectFromDER($data, $this->_contentOffset);
        $this->_der = $data;
        $this->_typeTag = $this->_identifier->intTag();
    }

    /**
     * {@inheritdoc}
     */
    public function typeClass(): int
    {
        return $this->_identifier->typeClass();
    }

    /**
     * {@inheritdoc}
     */
    public function isConstructed(): bool
    {
        return $this->_identifier->isConstructed();
    }

    /**
     * {@inheritdoc}
     */
    public function toDER(): string
    {
        return $this->_der;
    }

    /**
     * {@inheritdoc}
     */
    protected function _encodedContentDER(): string
    {
        // if there's no content payload
        if (strlen($this->_der) === $this->_contentOffset) {
            return '';
        }
        return substr($this->_der, $this->_contentOffset);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/Sop/ASN1/DERData.php`.

**Classes defined**: DERData

**Functions defined**: _encodedContentDER, typeClass, toDER, isConstructed, __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 90
- Code lines: 76
- Comment lines: 41
- Blank lines: -27

### Main Components

**Functions** (5):
- `__construct()`
- `_encodedContentDER()`
- `isConstructed()`
- `toDER()`
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
php php/static_dependencies/Sop/ASN1/DERData.php
```

