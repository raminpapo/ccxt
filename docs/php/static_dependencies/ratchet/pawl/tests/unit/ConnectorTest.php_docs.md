# Documentation: php/static_dependencies/ratchet/pawl/tests/unit/ConnectorTest.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/pawl/tests/unit/ConnectorTest.php`
- **Size**: 4,220 bytes
- **Lines**: 118
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

use PHPUnit\Framework\TestCase;
use Ratchet\Client\Connector;
use React\EventLoop\Loop;
use React\Promise\RejectedPromise;
use React\Promise\Promise;

class ConnectorTest extends TestCase
{
    public function testConstructWithoutLoopAssignsLoopAutomatically()
    {
        $factory = new Connector();

        $ref = new \ReflectionProperty($factory, '_loop');
        $ref->setAccessible(true);
        $loop = $ref->getValue($factory);

        $this->assertInstanceOf('React\EventLoop\LoopInterface', $loop);
    }

    public function uriDataProvider() {
        return [
            ['ws://127.0.0.1', 'tcp://127.0.0.1:80'],
            ['wss://127.0.0.1', 'tls://127.0.0.1:443'],
            ['ws://127.0.0.1:1234', 'tcp://127.0.0.1:1234'],
            ['wss://127.0.0.1:4321', 'tls://127.0.0.1:4321']
        ];
    }

    /**
     * @dataProvider uriDataProvider
     */
    public function testSecureConnectionUsesTlsScheme($uri, $expectedConnectorUri) {
        $loop = Loop::get();

        $connector = $this->getMockBuilder('React\Socket\ConnectorInterface')->getMock();

        $connector->expects($this->once())
            ->method('connect')
            ->with($this->callback(function ($uri) use ($expectedConnectorUri) {
                return $uri === $expectedConnectorUri;
            }))
            // reject the promise so that we don't have to mock a connection here
            ->willReturn(new RejectedPromise(new Exception('')));

        $pawlConnector = new Connector($loop, $connector);

        $pawlConnector($uri);
    }

    public function testConnectorRejectsWhenUnderlyingSocketConnectorRejects()
    {
        $exception = new RuntimeException('Connection failed');

        $loop = $this->getMockBuilder('React\EventLoop\LoopInterface')->getMock();
        $connector = $this->getMockBuilder('React\Socket\ConnectorInterface')->getMock();
        $connector->expects($this->once())->method('connect')->willReturn(\React\Promise\reject($exception));

        $pawlConnector = new Connector($loop, $connector);

        $promise = $pawlConnector('ws://localhost');

        $actual = null;
        $promise->then(null, function ($reason) use (&$actual) {
            $actual = $reason;
        });
        $this->assertSame($exception, $actual);
    }

    public function testCancelConnectorShouldCancelUnderlyingSocketConnectorWhenSocketConnectionIsPending()
    {
        $promise = new Promise(function () { }, function () use (&$cancelled) {
            ++$cancelled;
        });

        $loop = $this->getMockBuilder('React\EventLoop\LoopInterface')->getMock();
        $connector = $this->getMockBuilder('React\Socket\ConnectorInterface')->getMock();
        $connector->expects($this->once())->method('connect')->willReturn($promise);

        $pawlConnector = new Connector($loop, $connector);

        $promise = $pawlConnector('ws://localhost');

        $this->assertNull($cancelled);
        $promise->cancel();
        $this->assertEquals(1, $cancelled);

        $message = null;
        $promise->then(null, function ($reason) use (&$message) {
            $message = $reason->getMessage();
        });
        $this->assertEquals('Connection to ws://localhost cancelled during handshake', $message);
    }

    public function testCancelConnectorShouldCloseUnderlyingSocketConnectionWhenHandshakeIsPending()
    {
        $connection = $this->getMockBuilder('React\Socket\ConnectionInterface')->getMock();
        $connection->expects($this->once())->method('close');

        $loop = $this->getMockBuilder('React\EventLoop\LoopInterface')->getMock();
        $connector = $this->getMockBuilder('React\Socket\ConnectorInterface')->getMock();
        $connector->expects($this->once())->method('connect')->willReturn(\React\Promise\resolve($connection));

        $pawlConnector = new Connector($loop, $connector);

        $promise = $pawlConnector('ws://localhost');

        $promise->cancel();

        $message = null;
        $promise->then(null, function ($reason) use (&$message) {
            $message = $reason->getMessage();
        });
        $this->assertEquals('Connection to ws://localhost cancelled during handshake', $message);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/pawl/tests/unit/ConnectorTest.php`.

**Classes defined**: ConnectorTest

**Functions defined**: testCancelConnectorShouldCancelUnderlyingSocketConnectorWhenSocketConnectionIsPending, uriDataProvider, testConstructWithoutLoopAssignsLoopAutomatically, testSecureConnectionUsesTlsScheme, testConnectorRejectsWhenUnderlyingSocketConnectorRejects, testCancelConnectorShouldCloseUnderlyingSocketConnectionWhenHandshakeIsPending

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 118
- Code lines: 89
- Comment lines: 4
- Blank lines: 25

### Main Components

**Functions** (6):
- `testCancelConnectorShouldCancelUnderlyingSocketConnectorWhenSocketConnectionIsPending()`
- `testCancelConnectorShouldCloseUnderlyingSocketConnectionWhenHandshakeIsPending()`
- `testConnectorRejectsWhenUnderlyingSocketConnectorRejects()`
- `testConstructWithoutLoopAssignsLoopAutomatically()`
- `testSecureConnectionUsesTlsScheme()`
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
