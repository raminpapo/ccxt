# Documentation: php/static_dependencies/ratchet/rfc6455/tests/unit/Handshake/PermessageDeflateOptionsTest.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/tests/unit/Handshake/PermessageDeflateOptionsTest.php`
- **Size**: 802 bytes
- **Lines**: 30
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Ratchet\RFC6455\Test\Unit\Handshake;

use Ratchet\RFC6455\Handshake\PermessageDeflateOptions;
use PHPUnit\Framework\TestCase;

class PermessageDeflateOptionsTest extends TestCase
{
    public static function versionSupportProvider() {
        return [
            ['7.0.17', false],
            ['7.0.18', true],
            ['7.0.200', true],
            ['5.6.0', false],
            ['7.1.3', false],
            ['7.1.4', true],
            ['7.1.200', true],
            ['10.0.0', true]
        ];
    }

    /**
     * @requires function deflate_init
     * @dataProvider versionSupportProvider
     */
    public function testVersionSupport($version, $supported) {
        $this->assertEquals($supported, PermessageDeflateOptions::permessageDeflateSupported($version));
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/tests/unit/Handshake/PermessageDeflateOptionsTest.php`.

**Classes defined**: PermessageDeflateOptionsTest

**Functions defined**: deflate_init, testVersionSupport, versionSupportProvider

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 26
- Comment lines: 4
- Blank lines: 0

### Main Components

**Functions** (3):
- `deflate_init()`
- `testVersionSupport()`
- `versionSupportProvider()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
