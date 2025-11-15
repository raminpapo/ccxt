# Documentation: php/static_dependencies/ratchet/rfc6455/tests/unit/Handshake/ResponseVerifierTest.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/tests/unit/Handshake/ResponseVerifierTest.php`
- **Size**: 985 bytes
- **Lines**: 40
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Ratchet\RFC6455\Test\Unit\Handshake;

use Ratchet\RFC6455\Handshake\ResponseVerifier;
use PHPUnit\Framework\TestCase;

/**
 * @covers Ratchet\RFC6455\Handshake\ResponseVerifier
 */
class ResponseVerifierTest extends TestCase {
    /**
     * @var ResponseVerifier
     */
    protected $_v;

    public function setUp() {
        $this->_v = new ResponseVerifier;
    }

    public static function subProtocolsProvider() {
        return [
            [true,  ['a'], ['a']]
          , [true,  ['c', 'd', 'a'], ['a']]
          , [true,  ['c, a', 'd'], ['a']]
          , [true,  [], []]
          , [true,  ['a', 'b'], []]
          , [false, ['c', 'd', 'a'], ['b', 'a']]
          , [false, ['a', 'b', 'c'], ['d']]
        ];
    }

    /**
     * @dataProvider subProtocolsProvider
     */
    public function testVerifySubProtocol($expected, $request, $response) {
        $this->assertEquals($expected, $this->_v->verifySubProtocol($request, $response));
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/tests/unit/Handshake/ResponseVerifierTest.php`.

**Classes defined**: ResponseVerifierTest

**Functions defined**: subProtocolsProvider, testVerifySubProtocol, setUp

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 33
- Comment lines: 9
- Blank lines: -2

### Main Components

**Functions** (3):
- `setUp()`
- `subProtocolsProvider()`
- `testVerifySubProtocol()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
