# Documentation: php/static_dependencies/MessagePack/Type/Timestamp.php

## File Metadata

- **Path**: `php/static_dependencies/MessagePack/Type/Timestamp.php`
- **Size**: 1,022 bytes
- **Lines**: 47
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

final class Timestamp
{
    private $seconds;
    private $nanoseconds;

    public function __construct(int $seconds, int $nanoseconds = 0)
    {
        $this->seconds = $seconds;
        $this->nanoseconds = $nanoseconds;
    }

    public static function now() : self
    {
        $date = new \DateTime();

        return new self($date->getTimestamp(), (int) $date->format('u') * 1000);
    }

    public static function fromDateTime(\DateTimeInterface $date) : self
    {
        return new self($date->getTimestamp(), (int) $date->format('u') * 1000);
    }

    public function getSeconds() : int
    {
        return $this->seconds;
    }

    public function getNanoseconds() : int
    {
        return $this->nanoseconds;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/MessagePack/Type/Timestamp.php`.

**Classes defined**: Timestamp

**Functions defined**: getSeconds, __construct, getNanoseconds, now, fromDateTime

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 37
- Comment lines: 8
- Blank lines: 2

### Main Components

**Classes** (1):
- `Timestamp`

**Functions** (5):
- `__construct()`
- `fromDateTime()`
- `getNanoseconds()`
- `getSeconds()`
- `now()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/MessagePack/Type/Timestamp.php
```

