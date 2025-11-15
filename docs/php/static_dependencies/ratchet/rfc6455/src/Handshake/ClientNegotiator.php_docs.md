# Documentation: php/static_dependencies/ratchet/rfc6455/src/Handshake/ClientNegotiator.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/src/Handshake/ClientNegotiator.php`
- **Size**: 2,569 bytes
- **Lines**: 72
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Ratchet\RFC6455\Handshake;
use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\UriInterface;
use GuzzleHttp\Psr7\Request;

class ClientNegotiator {
    /**
     * @var ResponseVerifier
     */
    private $verifier;

    /**
     * @var \Psr\Http\Message\RequestInterface
     */
    private $defaultHeader;

    function __construct(?PermessageDeflateOptions $perMessageDeflateOptions = null) {
        $this->verifier = new ResponseVerifier;

        $this->defaultHeader = new Request('GET', '', [
            'Connection'            => 'Upgrade'
          , 'Upgrade'               => 'websocket'
          , 'Sec-WebSocket-Version' => $this->getVersion()
          , 'User-Agent'            => "Ratchet"
        ]);

        if ($perMessageDeflateOptions === null) {
            $perMessageDeflateOptions = PermessageDeflateOptions::createDisabled();
        }

        // https://bugs.php.net/bug.php?id=73373
        // https://bugs.php.net/bug.php?id=74240 - need >=7.1.4 or >=7.0.18
        if ($perMessageDeflateOptions->isEnabled() &&
            !PermessageDeflateOptions::permessageDeflateSupported()) {
            trigger_error('permessage-deflate is being disabled because it is not support by your PHP version.', E_USER_NOTICE);
            $perMessageDeflateOptions = PermessageDeflateOptions::createDisabled();
        }
        if ($perMessageDeflateOptions->isEnabled() && !function_exists('deflate_add')) {
            trigger_error('permessage-deflate is being disabled because you do not have the zlib extension.', E_USER_NOTICE);
            $perMessageDeflateOptions = PermessageDeflateOptions::createDisabled();
        }

        $this->defaultHeader = $perMessageDeflateOptions->addHeaderToRequest($this->defaultHeader);
    }

    public function generateRequest(UriInterface $uri) {
        return $this->defaultHeader->withUri($uri)
            ->withHeader("Sec-WebSocket-Key", $this->generateKey());
    }

    public function validateResponse(RequestInterface $request, ResponseInterface $response) {
        return $this->verifier->verifyAll($request, $response);
    }

    public function generateKey() {
        $chars     = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwzyz1234567890+/=';
        $charRange = strlen($chars) - 1;
        $key       = '';
        for ($i = 0; $i < 16; $i++) {
            $key .= $chars[mt_rand(0, $charRange)];
        }

        return base64_encode($key);
    }

    public function getVersion() {
        return 13;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/src/Handshake/ClientNegotiator.php`.

**Classes defined**: ClientNegotiator

**Functions defined**: validateResponse, generateRequest, getVersion, generateKey, __construct

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 57
- Comment lines: 8
- Blank lines: 7

### Main Components

**Classes** (1):
- `ClientNegotiator`

**Functions** (5):
- `__construct()`
- `generateKey()`
- `generateRequest()`
- `getVersion()`
- `validateResponse()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ratchet/rfc6455/src/Handshake/ClientNegotiator.php
```

