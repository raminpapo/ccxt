# Documentation: php/static_dependencies/ratchet/rfc6455/tests/unit/Messaging/MessageTest.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/tests/unit/Messaging/MessageTest.php`
- **Size**: 1,948 bytes
- **Lines**: 61
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Ratchet\RFC6455\Test\Unit\Messaging;

use Ratchet\RFC6455\Messaging\Frame;
use Ratchet\RFC6455\Messaging\Message;
use PHPUnit\Framework\TestCase;

/**
 * @covers Ratchet\RFC6455\Messaging\Message
 */
class MessageTest extends TestCase {
    /** @var Message */
    protected $message;

    public function setUp() {
        $this->message = new Message;
    }

    public function testNoFrames() {
        $this->assertFalse($this->message->isCoalesced());
    }

    public function testNoFramesOpCode() {
        $this->setExpectedException('UnderflowException');
        $this->message->getOpCode();
    }

    public function testFragmentationPayload() {
        $a = 'Hello ';
        $b = 'World!';
        $f1 = new Frame($a, false);
        $f2 = new Frame($b, true, Frame::OP_CONTINUE);
        $this->message->addFrame($f1)->addFrame($f2);
        $this->assertEquals(strlen($a . $b), $this->message->getPayloadLength());
        $this->assertEquals($a . $b, $this->message->getPayload());
    }

    public function testUnbufferedFragment() {
        $this->message->addFrame(new Frame('The quick brow', false));
        $this->setExpectedException('UnderflowException');
        $this->message->getPayload();
    }

    public function testGetOpCode() {
        $this->message
            ->addFrame(new Frame('The quick brow', false, Frame::OP_TEXT))
            ->addFrame(new Frame('n fox jumps ov', false, Frame::OP_CONTINUE))
            ->addFrame(new Frame('er the lazy dog', true, Frame::OP_CONTINUE))
        ;
        $this->assertEquals(Frame::OP_TEXT, $this->message->getOpCode());
    }

    public function testGetUnBufferedPayloadLength() {
        $this->message
            ->addFrame(new Frame('The quick brow', false, Frame::OP_TEXT))
            ->addFrame(new Frame('n fox jumps ov', false, Frame::OP_CONTINUE))
        ;
        $this->assertEquals(28, $this->message->getPayloadLength());
    }
}
```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/tests/unit/Messaging/MessageTest.php`.

**Classes defined**: MessageTest

**Functions defined**: testGetOpCode, setUp, testUnbufferedFragment, testFragmentationPayload, testNoFramesOpCode, testNoFrames, testGetUnBufferedPayloadLength

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 51
- Comment lines: 4
- Blank lines: 6

### Main Components

**Functions** (7):
- `setUp()`
- `testFragmentationPayload()`
- `testGetOpCode()`
- `testGetUnBufferedPayloadLength()`
- `testNoFrames()`
- `testNoFramesOpCode()`
- `testUnbufferedFragment()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
