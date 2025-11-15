# Documentation: php/static_dependencies/ratchet/pawl/tests/autobahn/runner.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/pawl/tests/autobahn/runner.php`
- **Size**: 1,991 bytes
- **Lines**: 68
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
use Ratchet\Client\WebSocket;
use React\Promise\Deferred;

    require __DIR__ . '/../../vendor/autoload.php';

    define('AGENT', 'Pawl/0.4');

    $connFactory = function() {
        $connector = new Ratchet\Client\Connector();

        return function($url) use ($connector) {
            return $connector('ws://127.0.0.1:9001' . $url);
        };
    };

    $connector = $connFactory();

    $connector('/getCaseCount')
        ->then(function(WebSocket $conn) {
            $futureNum = new Deferred;

            $conn->on('message', function($msg) use ($futureNum) {
                $futureNum->resolve($msg);
            });

            return $futureNum->promise();
        }, function($e) {
            echo "Could not connect to test server: {$e->getMessage()}\n";
        })->then(function($numOfCases) use ($connector) {
            echo "Running {$numOfCases} test cases\n\n";

            $allCases = new Deferred;

            $i = 0;

            $runNextCase = function() use (&$runNextCase, &$i, $numOfCases, $allCases, $connector) {
                $i++;

                if ($i > (int)$numOfCases->getPayload()) {
                    $allCases->resolve();

                    return;
                }

                echo ".";

                $connector("/runCase?case={$i}&agent=" . AGENT)->then(function(WebSocket $conn) use ($runNextCase) {
                    $conn->on('message', function($msg, $conn) {
                        $conn->send($msg);
                    });

                    $conn->on('close', $runNextCase);
                });
            };

            $runNextCase();

            return $allCases->promise();
        })->then(function() use ($connector) {
            $connector('/updateReports?agent=' . AGENT)->then(function(WebSocket $conn) {
                echo "\nDone!\n";
                $conn->on('close', function () {
                    \React\EventLoop\Loop::stop();
                });
            });
        });

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/pawl/tests/autobahn/runner.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 68
- Code lines: 49
- Comment lines: 0
- Blank lines: 19

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/../../vendor/autoload.php` (imported)
- `/../../vendor/autoload.php` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
