# Documentation: php/static_dependencies/MessagePack/MessagePack.php

## File Metadata

- **Path**: `php/static_dependencies/MessagePack/MessagePack.php`
- **Size**: 1,516 bytes
- **Lines**: 63
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

namespace MessagePack;

use MessagePack\Exception\InvalidOptionException;
use MessagePack\Exception\PackingFailedException;
use MessagePack\Exception\UnpackingFailedException;
use MessagePack\Extension\TimestampExtension;

final class MessagePack
{
    /** @var Extension[]|null */
    private static $extensions;

    /**
     * @codeCoverageIgnore
     */
    private function __construct()
    {
    }

    /**
     * @param mixed $value
     * @param PackOptions|int|null $options
     *
     * @throws InvalidOptionException
     * @throws PackingFailedException
     */
    public static function pack($value, $options = null) : string
    {
        return (new Packer($options, self::getBuiltInExtensions()))->pack($value);
    }

    /**
     * @param UnpackOptions|int|null $options
     *
     * @throws InvalidOptionException
     * @throws UnpackingFailedException
     *
     * @return mixed
     */
    public static function unpack(string $data, $options = null)
    {
        return (new BufferUnpacker($data, $options, self::getBuiltInExtensions()))->unpack();
    }

    private static function getBuiltInExtensions() : array
    {
        return self::$extensions ?? self::$extensions = [
            new TimestampExtension(),
        ];
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/MessagePack/MessagePack.php`.

**Classes defined**: MessagePack

**Functions defined**: __construct, pack, getBuiltInExtensions, unpack

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 54
- Comment lines: 27
- Blank lines: -18

### Main Components

**Classes** (1):
- `MessagePack`

**Functions** (4):
- `__construct()`
- `getBuiltInExtensions()`
- `pack()`
- `unpack()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/MessagePack/MessagePack.php
```

