# Documentation: php/static_dependencies/ringcentral-psr7/src/StreamDecoratorTrait.php

## File Metadata

- **Path**: `php/static_dependencies/ringcentral-psr7/src/StreamDecoratorTrait.php`
- **Size**: 3,061 bytes
- **Lines**: 140
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace RingCentral\Psr7;

use Psr\Http\Message\StreamInterface;

/**
 * Stream decorator trait
 * @property StreamInterface stream
 */
abstract class StreamDecoratorTrait implements StreamInterface
{
    /**
     * @param StreamInterface|null $stream Stream to decorate
     */
    public function __construct(?StreamInterface $stream = null)
    {
        if ($stream) $this->stream = $stream;
    }

    /**
     * Magic method used to create a new stream if streams are not added in
     * the constructor of a decorator (e.g., LazyOpenStream).
     *
     * @param string $name Name of the property (allows "stream" only).
     *
     * @return StreamInterface
     */
    public function __get($name)
    {
        if ($name == 'stream') {
            $this->stream = $this->createStream();
            return $this->stream;
        }

        throw new \UnexpectedValueException("$name not found on class");
    }

    public function __toString()
    {
        try {
            if ($this->isSeekable()) {
                $this->seek(0);
            }
            return $this->getContents();
        } catch (\Exception $e) {
            // Really, PHP? https://bugs.php.net/bug.php?id=53648
            trigger_error('StreamDecorator::__toString exception: '
                . (string) $e, E_USER_ERROR);
            return '';
        }
    }

    public function getContents()
    {
        return copy_to_string($this);
    }

    /**
     * Allow decorators to implement custom methods
     *
     * @param string $method Missing method name
     * @param array  $args   Method arguments
     *
     * @return mixed
     */
    public function __call($method, array $args)
    {
        $result = call_user_func_array(array($this->stream, $method), $args);

        // Always return the wrapped object if the result is a return $this
        return $result === $this->stream ? $this : $result;
    }

    public function close()
    {
        $this->stream->close();
    }

    public function getMetadata($key = null)
    {
        return $this->stream->getMetadata($key);
    }

    public function detach()
    {
        return $this->stream->detach();
    }

    public function getSize()
    {
        return $this->stream->getSize();
    }

    public function eof()
    {
        return $this->stream->eof();
    }

    public function tell()
    {
        return $this->stream->tell();
    }

    public function isReadable()
    {
        return $this->stream->isReadable();
    }

    public function isWritable()
    {
        return $this->stream->isWritable();
    }

    public function isSeekable()
    {
        return $this->stream->isSeekable();
    }

    public function rewind()
    {
        $this->seek(0);
    }

    public function seek($offset, $whence = SEEK_SET)
    {
        $this->stream->seek($offset, $whence);
    }

    public function read($length)
    {
        return $this->stream->read($length);
    }

    public function write($string)
    {
        return $this->stream->write($string);
    }

}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ringcentral-psr7/src/StreamDecoratorTrait.php`.

**Classes defined**: StreamDecoratorTrait

**Functions defined**: getSize, getContents, __call, __toString, __construct, __get, eof, detach, getMetadata, close

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 140
- Code lines: 115
- Comment lines: 25
- Blank lines: 0

### Main Components

**Functions** (18):
- `__call()`
- `__construct()`
- `__get()`
- `__toString()`
- `close()`
- `detach()`
- `eof()`
- `getContents()`
- `getMetadata()`
- `getSize()`
- `isReadable()`
- `isSeekable()`
- `isWritable()`
- `read()`
- `rewind()`
- `seek()`
- `tell()`
- `write()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/ringcentral-psr7/src/StreamDecoratorTrait.php
```

