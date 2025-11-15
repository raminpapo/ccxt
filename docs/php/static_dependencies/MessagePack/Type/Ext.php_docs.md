# Documentation: php/static_dependencies/MessagePack/Type/Ext.php

## File Metadata

- **Path**: `php/static_dependencies/MessagePack/Type/Ext.php`
- **Size**: 706 bytes
- **Lines**: 36
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

final class Ext implements CanBePacked
{
    /** @readonly */
    public $type;

    /** @readonly */
    public $data;

    public function __construct(int $type, string $data)
    {
        $this->type = $type;
        $this->data = $data;
    }

    public function pack(Packer $packer) : string
    {
        return $packer->packExt($this->type, $this->data);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/MessagePack/Type/Ext.php`.

**Classes defined**: Ext

**Functions defined**: __construct, pack

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 28
- Comment lines: 10
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
php php/static_dependencies/MessagePack/Type/Ext.php
```

