# Documentation: php/static_dependencies/ratchet/rfc6455/src/Handshake/NegotiatorInterface.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/src/Handshake/NegotiatorInterface.php`
- **Size**: 1,581 bytes
- **Lines**: 48
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Ratchet\RFC6455\Handshake;
use Psr\Http\Message\RequestInterface;

/**
 * A standard interface for interacting with the various version of the WebSocket protocol
 * @todo Look in to extension support
 */
interface NegotiatorInterface {
    const GUID = '258EAFA5-E914-47DA-95CA-C5AB0DC85B11';

    /**
     * Given an HTTP header, determine if this version should handle the protocol
     * @param RequestInterface $request
     * @return bool
     */
    function isProtocol(RequestInterface $request);

    /**
     * Although the version has a name associated with it the integer returned is the proper identification
     * @return int
     */
    function getVersionNumber();

    /**
     * Perform the handshake and return the response headers
     * @param RequestInterface $request
     * @return \Psr\Http\Message\ResponseInterface
     */
    function handshake(RequestInterface $request);

    /**
     * Add supported protocols. If the request has any matching the response will include one
     * @param array $protocols
     */
    function setSupportedSubProtocols(array $protocols);

    /**
     * If enabled and support for a subprotocol has been added handshake
     *  will not upgrade if a match between request and supported subprotocols
     * @param boolean $enable
     * @todo Consider extending this interface and moving this there.
     *       The spec does says the server can fail for this reason, but
     *       it is not a requirement. This is an implementation detail.
     */
    function setStrictSubProtocolCheck($enable);
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/src/Handshake/NegotiatorInterface.php`.

**Functions defined**: isProtocol, handshake, getVersionNumber, setSupportedSubProtocols, setStrictSubProtocolCheck

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 41
- Comment lines: 30
- Blank lines: -23

### Main Components

**Functions** (5):
- `getVersionNumber()`
- `handshake()`
- `isProtocol()`
- `setStrictSubProtocolCheck()`
- `setSupportedSubProtocols()`

**Constants** (1):
- `GUID`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ratchet/rfc6455/src/Handshake/NegotiatorInterface.php
```

