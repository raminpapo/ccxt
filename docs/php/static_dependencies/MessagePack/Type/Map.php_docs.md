# Documentation: php/static_dependencies/MessagePack/Type/Map.php

## File Metadata

- **Path**: `php/static_dependencies/MessagePack/Type/Map.php`
- **Size**: 607 bytes
- **Lines**: 32
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

namespace MessagePack\Type;

use MessagePack\CanBePacked;
use MessagePack\Packer;

final class Map implements CanBePacked
{
    /** @readonly */
    public $map;

    public function __construct(array $map)
    {
        $this->map = $map;
    }

    public function pack(Packer $packer) : string
    {
        return $packer->packMap($this->map);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/MessagePack/Type/Map.php`.

**Classes defined**: Map

**Functions defined**: __construct, pack

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 25
- Comment lines: 9
- Blank lines: -2

### Main Components

**Functions** (2):
- `__construct()`
- `pack()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/MessagePack/Type/Map.php
```

