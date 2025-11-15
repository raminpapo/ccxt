# Documentation: php/static_dependencies/MessagePack/TypeTransformer/StreamTransformer.php

## File Metadata

- **Path**: `php/static_dependencies/MessagePack/TypeTransformer/StreamTransformer.php`
- **Size**: 619 bytes
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

namespace MessagePack\TypeTransformer;

use MessagePack\CanPack;
use MessagePack\Packer;

class StreamTransformer implements CanPack
{
    public function pack(Packer $packer, $value) : ?string
    {
        return \is_resource($value) && 'stream' === \get_resource_type($value)
            ? $packer->packBin(\stream_get_contents($value))
            : null;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/MessagePack/TypeTransformer/StreamTransformer.php`.

**Classes defined**: StreamTransformer

**Functions defined**: pack

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 21
- Comment lines: 8
- Blank lines: -3

### Main Components

**Functions** (1):
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
php php/static_dependencies/MessagePack/TypeTransformer/StreamTransformer.php
```

