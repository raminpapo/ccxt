# Documentation: php/static_dependencies/ratchet/rfc6455/src/Handshake/PermessageDeflateOptions.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/src/Handshake/PermessageDeflateOptions.php`
- **Size**: 8,411 bytes
- **Lines**: 267
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Ratchet\RFC6455\Handshake;

use Psr\Http\Message\MessageInterface;
use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;

final class PermessageDeflateOptions
{
    const MAX_WINDOW_BITS = 15;
    /* this is a private instead of const for 5.4 compatibility */
    private static $VALID_BITS = ['8', '9', '10', '11', '12', '13', '14', '15'];

    private $deflateEnabled = false;

    private $server_no_context_takeover;
    private $client_no_context_takeover;
    private $server_max_window_bits;
    private $client_max_window_bits;

    private function __construct() { }

    public static function createEnabled() {
        $new                             = new static();
        $new->deflateEnabled             = true;
        $new->client_max_window_bits     = self::MAX_WINDOW_BITS;
        $new->client_no_context_takeover = false;
        $new->server_max_window_bits     = self::MAX_WINDOW_BITS;
        $new->server_no_context_takeover = false;

        return $new;
    }

    public static function createDisabled() {
        return new static();
    }

    public function withClientNoContextTakeover() {
        $new = clone $this;
        $new->client_no_context_takeover = true;
        return $new;
    }

    public function withoutClientNoContextTakeover() {
        $new = clone $this;
        $new->client_no_context_takeover = false;
        return $new;
    }

    public function withServerNoContextTakeover() {
        $new = clone $this;
        $new->server_no_context_takeover = true;
        return $new;
    }

    public function withoutServerNoContextTakeover() {
        $new = clone $this;
        $new->server_no_context_takeover = false;
        return $new;
    }

    public function withServerMaxWindowBits($bits = self::MAX_WINDOW_BITS) {
        if (!in_array($bits, self::$VALID_BITS)) {
            throw new \Exception('server_max_window_bits must have a value between 8 and 15.');
        }
        $new = clone $this;
        $new->server_max_window_bits = $bits;
        return $new;
    }

    public function withClientMaxWindowBits($bits = self::MAX_WINDOW_BITS) {
        if (!in_array($bits, self::$VALID_BITS)) {
            throw new \Exception('client_max_window_bits must have a value between 8 and 15.');
        }
        $new = clone $this;
        $new->client_max_window_bits = $bits;
        return $new;
    }

    /**
     * https://tools.ietf.org/html/rfc6455#section-9.1
     * https://tools.ietf.org/html/rfc7692#section-7
     *
     * @param MessageInterface $requestOrResponse
     * @return PermessageDeflateOptions[]
     * @throws \Exception
     */
    public static function fromRequestOrResponse(MessageInterface $requestOrResponse) {
        $optionSets = [];

        $extHeader = preg_replace('/\s+/', '', join(', ', $requestOrResponse->getHeader('Sec-Websocket-Extensions')));

        $configurationRequests = explode(',', $extHeader);
        foreach ($configurationRequests as $configurationRequest) {
            $parts = explode(';', $configurationRequest);
            if (count($parts) == 0) {
                continue;
            }

            if ($parts[0] !== 'permessage-deflate') {
                continue;
            }

            array_shift($parts);
            $options                 = new static();
            $options->deflateEnabled = true;
            foreach ($parts as $part) {
                $kv = explode('=', $part);
                $key = $kv[0];
                $value = count($kv) > 1 ? $kv[1] : null;

                switch ($key) {
                    case "server_no_context_takeover":
                    case "client_no_context_takeover":
                        if ($value !== null) {
                            throw new InvalidPermessageDeflateOptionsException($key . ' must not have a value.');
                        }
                        $value = true;
                        break;
                    case "server_max_window_bits":
                        if (!in_array($value, self::$VALID_BITS)) {
                            throw new InvalidPermessageDeflateOptionsException($key . ' must have a value between 8 and 15.');
                        }
                        break;
                    case "client_max_window_bits":
                        if ($value === null) {
                            $value = '15';
                        }
                        if (!in_array($value, self::$VALID_BITS)) {
                            throw new InvalidPermessageDeflateOptionsException($key . ' must have no value or a value between 8 and 15.');
                        }
                        break;
                    default:
                        throw new InvalidPermessageDeflateOptionsException('Option "' . $key . '"is not valid for permessage deflate');
                }

                if ($options->$key !== null) {
                    throw new InvalidPermessageDeflateOptionsException($key . ' specified more than once. Connection must be declined.');
                }

                $options->$key = $value;
            }

            if ($options->getClientMaxWindowBits() === null) {
                $options->client_max_window_bits = 15;
            }

            if ($options->getServerMaxWindowBits() === null) {
                $options->server_max_window_bits = 15;
            }

            $optionSets[] = $options;
        }

        // always put a disabled on the end
        $optionSets[] = new static();

        return $optionSets;
    }

    /**
     * @return mixed
     */
    public function getServerNoContextTakeover()
    {
        return $this->server_no_context_takeover;
    }

    /**
     * @return mixed
     */
    public function getClientNoContextTakeover()
    {
        return $this->client_no_context_takeover;
    }

    /**
     * @return mixed
     */
    public function getServerMaxWindowBits()
    {
        return $this->server_max_window_bits;
    }

    /**
     * @return mixed
     */
    public function getClientMaxWindowBits()
    {
        return $this->client_max_window_bits;
    }

    /**
     * @return bool
     */
    public function isEnabled()
    {
        return $this->deflateEnabled;
    }

    /**
     * @param ResponseInterface $response
     * @return ResponseInterface
     */
    public function addHeaderToResponse(ResponseInterface $response)
    {
        if (!$this->deflateEnabled) {
            return $response;
        }

        $header = 'permessage-deflate';
        if ($this->client_max_window_bits != 15) {
            $header .= '; client_max_window_bits='. $this->client_max_window_bits;
        }
        if ($this->client_no_context_takeover) {
            $header .= '; client_no_context_takeover';
        }
        if ($this->server_max_window_bits != 15) {
            $header .= '; server_max_window_bits=' . $this->server_max_window_bits;
        }
        if ($this->server_no_context_takeover) {
            $header .= '; server_no_context_takeover';
        }

        return $response->withAddedHeader('Sec-Websocket-Extensions', $header);
    }

    public function addHeaderToRequest(RequestInterface $request) {
        if (!$this->deflateEnabled) {
            return $request;
        }

        $header = 'permessage-deflate';
        if ($this->server_no_context_takeover) {
            $header .= '; server_no_context_takeover';
        }
        if ($this->client_no_context_takeover) {
            $header .= '; client_no_context_takeover';
        }
        if ($this->server_max_window_bits != 15) {
            $header .= '; server_max_window_bits=' . $this->server_max_window_bits;
        }
        $header .= '; client_max_window_bits';
        if ($this->client_max_window_bits != 15) {
            $header .= '='. $this->client_max_window_bits;
        }

        return $request->withAddedHeader('Sec-Websocket-Extensions', $header);
    }

    public static function permessageDeflateSupported($version = PHP_VERSION) {
        if (!function_exists('deflate_init')) {
            return false;
        }
        if (version_compare($version, '7.1.3', '>')) {
            return true;
        }
        if (version_compare($version, '7.0.18', '>=')
            && version_compare($version, '7.1.0', '<')) {
            return true;
        }

        return false;
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/src/Handshake/PermessageDeflateOptions.php`.

**Classes defined**: PermessageDeflateOptions

**Functions defined**: createDisabled, withoutServerNoContextTakeover, fromRequestOrResponse, withClientMaxWindowBits, createEnabled, withServerNoContextTakeover, withServerMaxWindowBits, withClientNoContextTakeover, __construct, withoutClientNoContextTakeover

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 267
- Code lines: 224
- Comment lines: 29
- Blank lines: 14

### Main Components

**Classes** (1):
- `PermessageDeflateOptions`

**Functions** (18):
- `__construct()`
- `addHeaderToRequest()`
- `addHeaderToResponse()`
- `createDisabled()`
- `createEnabled()`
- `fromRequestOrResponse()`
- `getClientMaxWindowBits()`
- `getClientNoContextTakeover()`
- `getServerMaxWindowBits()`
- `getServerNoContextTakeover()`
- `isEnabled()`
- `permessageDeflateSupported()`
- `withClientMaxWindowBits()`
- `withClientNoContextTakeover()`
- `withServerMaxWindowBits()`
- `withServerNoContextTakeover()`
- `withoutClientNoContextTakeover()`
- `withoutServerNoContextTakeover()`

**Constants** (2):
- `MAX_WINDOW_BITS`
- `VALID_BITS`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ratchet/rfc6455/src/Handshake/PermessageDeflateOptions.php
```

