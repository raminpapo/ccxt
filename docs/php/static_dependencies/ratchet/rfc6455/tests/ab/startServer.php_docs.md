# Documentation: php/static_dependencies/ratchet/rfc6455/tests/ab/startServer.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/tests/ab/startServer.php`
- **Size**: 3,331 bytes
- **Lines**: 87
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

use GuzzleHttp\Psr7\Message;
use GuzzleHttp\Psr7\Response;
use Ratchet\RFC6455\Handshake\PermessageDeflateOptions;
use Ratchet\RFC6455\Messaging\MessageBuffer;
use Ratchet\RFC6455\Messaging\MessageInterface;
use Ratchet\RFC6455\Messaging\FrameInterface;
use Ratchet\RFC6455\Messaging\Frame;

require_once __DIR__ . "/../bootstrap.php";

$loop   = \React\EventLoop\Factory::create();

$socket = new \React\Socket\Server('0.0.0.0:9001', $loop);

$closeFrameChecker = new \Ratchet\RFC6455\Messaging\CloseFrameChecker;
$negotiator = new \Ratchet\RFC6455\Handshake\ServerNegotiator(new \Ratchet\RFC6455\Handshake\RequestVerifier, PermessageDeflateOptions::permessageDeflateSupported());

$uException = new \UnderflowException;


$socket->on('connection', function (React\Socket\ConnectionInterface $connection) use ($negotiator, $closeFrameChecker, $uException, $socket) {
    $headerComplete = false;
    $buffer = '';
    $parser = null;
    $connection->on('data', function ($data) use ($connection, &$parser, &$headerComplete, &$buffer, $negotiator, $closeFrameChecker, $uException, $socket) {
        if ($headerComplete) {
            $parser->onData($data);
            return;
        }

        $buffer .= $data;
        $parts = explode("\r\n\r\n", $buffer);
        if (count($parts) < 2) {
            return;
        }
        $headerComplete = true;
        $psrRequest = Message::parseRequest($parts[0] . "\r\n\r\n");
        $negotiatorResponse = $negotiator->handshake($psrRequest);

        $negotiatorResponse = $negotiatorResponse->withAddedHeader("Content-Length", "0");

        if ($negotiatorResponse->getStatusCode() !== 101 && $psrRequest->getUri()->getPath() === '/shutdown') {
            $connection->end(Message::toString(new Response(200, [], 'Shutting down echo server.' . PHP_EOL)));
            $socket->close();
            return;
        };

        $connection->write(Message::toString($negotiatorResponse));

        if ($negotiatorResponse->getStatusCode() !== 101) {
            $connection->end();
            return;
        }

        // there is no need to look through the client requests
        // we support any valid permessage deflate
        $deflateOptions = PermessageDeflateOptions::fromRequestOrResponse($psrRequest)[0];

        $parser = new \Ratchet\RFC6455\Messaging\MessageBuffer($closeFrameChecker,
            function (MessageInterface $message, MessageBuffer $messageBuffer) {
                $messageBuffer->sendMessage($message->getPayload(), true, $message->isBinary());
            }, function (FrameInterface $frame) use ($connection, &$parser) {
                switch ($frame->getOpCode()) {
                    case Frame::OP_CLOSE:
                        $connection->end($frame->getContents());
                        break;
                    case Frame::OP_PING:
                        $connection->write($parser->newFrame($frame->getPayload(), true, Frame::OP_PONG)->getContents());
                        break;
                }
            }, true, function () use ($uException) {
                return $uException;
            },
            null,
            null,
           [$connection, 'write'],
           $deflateOptions);

        array_shift($parts);
        $parser->onData(implode("\r\n\r\n", $parts));
    });
});

$loop->run();

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/tests/ab/startServer.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 67
- Comment lines: 2
- Blank lines: 18

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/../bootstrap.php` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
