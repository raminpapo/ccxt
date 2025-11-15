# Documentation: php/static_dependencies/MessagePack/Exception/InvalidOptionException.php

## File Metadata

- **Path**: `php/static_dependencies/MessagePack/Exception/InvalidOptionException.php`
- **Size**: 714 bytes
- **Lines**: 25
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

class InvalidOptionException extends \InvalidArgumentException
{
    public static function outOfRange(string $invalidOption, array $validOptions) : self
    {
        $use = \count($validOptions) > 2
            ? \sprintf('one of %2$s or %1$s', \array_pop($validOptions), \implode(', ', $validOptions))
            : \implode(' or ', $validOptions);

        return new self("Invalid option $invalidOption, use $use");
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/MessagePack/Exception/InvalidOptionException.php`.

**Classes defined**: InvalidOptionException

**Functions defined**: outOfRange

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 20
- Comment lines: 8
- Blank lines: -3

### Main Components

**Functions** (1):
- `outOfRange()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/MessagePack/Exception/InvalidOptionException.php
```

