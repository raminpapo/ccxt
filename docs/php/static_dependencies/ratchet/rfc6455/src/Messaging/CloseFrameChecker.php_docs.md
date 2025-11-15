# Documentation: php/static_dependencies/ratchet/rfc6455/src/Messaging/CloseFrameChecker.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/src/Messaging/CloseFrameChecker.php`
- **Size**: 643 bytes
- **Lines**: 25
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Ratchet\RFC6455\Messaging;

class CloseFrameChecker {
    private $validCloseCodes = [];

    public function __construct() {
        $this->validCloseCodes = [
            Frame::CLOSE_NORMAL,
            Frame::CLOSE_GOING_AWAY,
            Frame::CLOSE_PROTOCOL,
            Frame::CLOSE_BAD_DATA,
            Frame::CLOSE_BAD_PAYLOAD,
            Frame::CLOSE_POLICY,
            Frame::CLOSE_TOO_BIG,
            Frame::CLOSE_MAND_EXT,
            Frame::CLOSE_SRV_ERR,
        ];
    }

    public function __invoke($val) {
        return ($val >= 3000 && $val <= 4999) || in_array($val, $this->validCloseCodes);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/src/Messaging/CloseFrameChecker.php`.

**Classes defined**: CloseFrameChecker

**Functions defined**: __invoke, __construct



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 21
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `CloseFrameChecker`

**Functions** (2):
- `__construct()`
- `__invoke()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ratchet/rfc6455/src/Messaging/CloseFrameChecker.php
```

