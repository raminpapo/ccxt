# Documentation: php/static_dependencies/ratchet/pawl/tests/unit/RequestUriTest.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/pawl/tests/unit/RequestUriTest.php`
- **Size**: 1,226 bytes
- **Lines**: 39
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
/**
 * Created by claudio on 2018-12-31
 */

use PHPUnit\Framework\TestCase;
use React\EventLoop\Factory;
use Ratchet\Client\Connector;
use Psr\Http\Message\RequestInterface;

class RequestUriTest extends TestCase {
    protected static function getPrivateClassMethod($className, $methodName) {
        $class = new ReflectionClass($className);
        $method = $class->getMethod($methodName);
        $method->setAccessible(true);
        return $method;
    }

    function uriDataProvider() {
        return [
            ['ws://127.0.0.1/bla', 'http://127.0.0.1/bla'],
            ['wss://127.0.0.1/bla', 'https://127.0.0.1/bla'],
            ['ws://127.0.0.1:1234/bla', 'http://127.0.0.1:1234/bla'],
            ['wss://127.0.0.1:4321/bla', 'https://127.0.0.1:4321/bla']
        ];
    }

    /**
     * @dataProvider uriDataProvider
     */
    function testGeneratedRequestUri($uri, $expectedRequestUri) {
        $connector = new Connector();

        $generateRequest = self::getPrivateClassMethod('\Ratchet\Client\Connector', 'generateRequest');
        $request = $generateRequest->invokeArgs($connector, [$uri, [], []]);

        $this->assertEquals((string)$request->getUri(), $expectedRequestUri);
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/pawl/tests/unit/RequestUriTest.php`.

**Classes defined**: RequestUriTest

**Functions defined**: testGeneratedRequestUri, uriDataProvider, getPrivateClassMethod

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 33
- Comment lines: 6
- Blank lines: 0

### Main Components

**Functions** (3):
- `getPrivateClassMethod()`
- `testGeneratedRequestUri()`
- `uriDataProvider()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
