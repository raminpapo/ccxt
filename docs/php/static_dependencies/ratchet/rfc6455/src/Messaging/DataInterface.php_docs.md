# Documentation: php/static_dependencies/ratchet/rfc6455/src/Messaging/DataInterface.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/src/Messaging/DataInterface.php`
- **Size**: 672 bytes
- **Lines**: 35
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Ratchet\RFC6455\Messaging;

interface DataInterface {
    /**
     * Determine if the message is complete or still fragmented
     * @return bool
     */
    function isCoalesced();

    /**
     * Get the number of bytes the payload is set to be
     * @return int
     */
    function getPayloadLength();

    /**
     * Get the payload (message) sent from peer
     * @return string
     */
    function getPayload();

    /**
     * Get raw contents of the message
     * @return string
     */
    function getContents();

    /**
     * Should return the unmasked payload received from peer
     * @return string
     */
    function __toString();
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/src/Messaging/DataInterface.php`.

**Functions defined**: getContents, __toString, isCoalesced, getPayloadLength, getPayload

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 29
- Comment lines: 20
- Blank lines: -14

### Main Components

**Functions** (5):
- `__toString()`
- `getContents()`
- `getPayload()`
- `getPayloadLength()`
- `isCoalesced()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ratchet/rfc6455/src/Messaging/DataInterface.php
```

