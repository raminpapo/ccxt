# Documentation: php/static_dependencies/ratchet/rfc6455/src/Messaging/MessageInterface.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/src/Messaging/MessageInterface.php`
- **Size**: 383 bytes
- **Lines**: 21
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Ratchet\RFC6455\Messaging;

interface MessageInterface extends DataInterface, \Traversable, \Countable {
    /**
     * @param FrameInterface $fragment
     * @return MessageInterface
     */
    function addFrame(FrameInterface $fragment);

    /**
     * @return int
     */
    function getOpcode();

    /**
     * @return bool
     */
    function isBinary();
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/src/Messaging/MessageInterface.php`.

**Functions defined**: isBinary, getOpcode, addFrame

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 17
- Comment lines: 10
- Blank lines: -6

### Main Components

**Functions** (3):
- `addFrame()`
- `getOpcode()`
- `isBinary()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ratchet/rfc6455/src/Messaging/MessageInterface.php
```

