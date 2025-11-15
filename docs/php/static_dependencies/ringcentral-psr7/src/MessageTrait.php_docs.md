# Documentation: php/static_dependencies/ringcentral-psr7/src/MessageTrait.php

## File Metadata

- **Path**: `php/static_dependencies/ringcentral-psr7/src/MessageTrait.php`
- **Size**: 4,091 bytes
- **Lines**: 168
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace RingCentral\Psr7;

use Psr\Http\Message\StreamInterface;

/**
 * Trait implementing functionality common to requests and responses.
 */
abstract class MessageTrait
{
    /** @var array Cached HTTP header collection with lowercase key to values */
    protected $headers = array();

    /** @var array Actual key to list of values per header. */
    protected $headerLines = array();

    /** @var string */
    protected $protocol = '1.1';

    /** @var StreamInterface */
    protected $stream;

    public function getProtocolVersion()
    {
        return $this->protocol;
    }

    public function withProtocolVersion($version)
    {
        if ($this->protocol === $version) {
            return $this;
        }

        $new = clone $this;
        $new->protocol = $version;
        return $new;
    }

    public function getHeaders()
    {
        return $this->headerLines;
    }

    public function hasHeader($header)
    {
        return isset($this->headers[strtolower($header)]);
    }

    public function getHeader($header)
    {
        $name = strtolower($header);
        return isset($this->headers[$name]) ? $this->headers[$name] : array();
    }

    public function getHeaderLine($header)
    {
        return implode(', ', $this->getHeader($header));
    }

    public function withHeader($header, $value)
    {
        $new = clone $this;
        $header = trim($header);
        $name = strtolower($header);

        if (!is_array($value)) {
            $new->headers[$name] = array(trim($value));
        } else {
            $new->headers[$name] = $value;
            foreach ($new->headers[$name] as &$v) {
                $v = trim($v);
            }
        }

        // Remove the header lines.
        foreach (array_keys($new->headerLines) as $key) {
            if (strtolower($key) === $name) {
                unset($new->headerLines[$key]);
            }
        }

        // Add the header line.
        $new->headerLines[$header] = $new->headers[$name];

        return $new;
    }

    public function withAddedHeader($header, $value)
    {
        if (!$this->hasHeader($header)) {
            return $this->withHeader($header, $value);
        }

        $header = trim($header);
        $name = strtolower($header);

        $value = (array) $value;
        foreach ($value as &$v) {
            $v = trim($v);
        }

        $new = clone $this;
        $new->headers[$name] = array_merge($new->headers[$name], $value);
        $new->headerLines[$header] = array_merge($new->headerLines[$header], $value);

        return $new;
    }

    public function withoutHeader($header)
    {
        if (!$this->hasHeader($header)) {
            return $this;
        }

        $new = clone $this;
        $name = strtolower($header);
        unset($new->headers[$name]);

        foreach (array_keys($new->headerLines) as $key) {
            if (strtolower($key) === $name) {
                unset($new->headerLines[$key]);
            }
        }

        return $new;
    }

    public function getBody()
    {
        if (!$this->stream) {
            $this->stream = stream_for('');
        }

        return $this->stream;
    }

    public function withBody(StreamInterface $body)
    {
        if ($body === $this->stream) {
            return $this;
        }

        $new = clone $this;
        $new->stream = $body;
        return $new;
    }

    protected function setHeaders(array $headers)
    {
        $this->headerLines = $this->headers = array();
        foreach ($headers as $header => $value) {
            $header = trim($header);
            $name = strtolower($header);
            if (!is_array($value)) {
                $value = trim($value);
                $this->headers[$name][] = $value;
                $this->headerLines[$header][] = $value;
            } else {
                foreach ($value as $v) {
                    $v = trim($v);
                    $this->headers[$name][] = $v;
                    $this->headerLines[$header][] = $v;
                }
            }
        }
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ringcentral-psr7/src/MessageTrait.php`.

**Classes defined**: MessageTrait

**Functions defined**: getHeaders, getProtocolVersion, withAddedHeader, hasHeader, getHeaderLine, withHeader, getBody, withoutHeader, withProtocolVersion, getHeader

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 168
- Code lines: 134
- Comment lines: 9
- Blank lines: 25

### Main Components

**Classes** (1):
- `MessageTrait`

**Functions** (12):
- `getBody()`
- `getHeader()`
- `getHeaderLine()`
- `getHeaders()`
- `getProtocolVersion()`
- `hasHeader()`
- `setHeaders()`
- `withAddedHeader()`
- `withBody()`
- `withHeader()`
- `withProtocolVersion()`
- `withoutHeader()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ringcentral-psr7/src/MessageTrait.php
```

