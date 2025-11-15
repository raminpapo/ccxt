# Documentation: php/static_dependencies/ratchet/rfc6455/src/Messaging/FrameInterface.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/src/Messaging/FrameInterface.php`
- **Size**: 650 bytes
- **Lines**: 39
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Ratchet\RFC6455\Messaging;

interface FrameInterface extends DataInterface {
    /**
     * Add incoming data to the frame from peer
     * @param string
     */
    function addBuffer($buf);

    /**
     * Is this the final frame in a fragmented message?
     * @return bool
     */
    function isFinal();

    /**
     * Is the payload masked?
     * @return bool
     */
    function isMasked();

    /**
     * @return int
     */
    function getOpcode();

    /**
     * @return int
     */
    //function getReceivedPayloadLength();

    /**
     * 32-big string
     * @return string
     */
    function getMaskingKey();
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/src/Messaging/FrameInterface.php`.

**Functions defined**: isFinal, getReceivedPayloadLength, getMaskingKey, isMasked, getOpcode, addBuffer

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 31
- Comment lines: 23
- Blank lines: -15

### Main Components

**Functions** (6):
- `addBuffer()`
- `getMaskingKey()`
- `getOpcode()`
- `getReceivedPayloadLength()`
- `isFinal()`
- `isMasked()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ratchet/rfc6455/src/Messaging/FrameInterface.php
```

