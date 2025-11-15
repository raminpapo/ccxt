# Documentation: php/static_dependencies/MessagePack/Exception/PackingFailedException.php

## File Metadata

- **Path**: `php/static_dependencies/MessagePack/Exception/PackingFailedException.php`
- **Size**: 663 bytes
- **Lines**: 26
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

/**
 * This file is part of the rybakit/msgpack.php package.
 *
 * (c) Eugene Leonovich <gen.work@gmail.com>
 *
 * For the full copyright and license information, please view the LICENSE
 * file that was distributed with this source code.
 */

namespace MessagePack\Exception;

class PackingFailedException extends \RuntimeException
{
    /**
     * @param mixed $value
     */
    public static function unsupportedType($value) : self
    {
        return new self(\sprintf('Unsupported type "%s", maybe you forgot to register the type transformer or extension?',
            \is_object($value) ? \get_class($value) : \gettype($value)
        ));
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/MessagePack/Exception/PackingFailedException.php`.

**Classes defined**: PackingFailedException

**Functions defined**: unsupportedType

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 22
- Comment lines: 11
- Blank lines: -7

### Main Components

**Functions** (1):
- `unsupportedType()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/MessagePack/Exception/PackingFailedException.php
```

