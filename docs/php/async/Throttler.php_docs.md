# Documentation: php/async/Throttler.php

## File Metadata

- **Path**: `php/async/Throttler.php`
- **Size**: 2,545 bytes
- **Lines**: 74
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt\async;

use React\Promise\Deferred;
use React\Promise\Promise;
use React\EventLoop\Loop;
use React\Async;

class Throttler {
    public $config;
    public $queue;
    public $running;

    public function __construct($config) {
        $this->config = array_merge(array(
            'refillRate' => 1.0,
            'delay' => 0.001,
            'cost' => 1.0,
            'tokens' => 0.0,
            'maxCapacity' => 2000,
            'capacity' => 1.0,
        ), $config);
        $this->queue = new \SplQueue();
        $this->running = false;
    }

    public function loop() {
        return Async\async(function () {
            $last_timestamp = microtime(true) * 1000.0;
            while ($this->running) {
                list($future, $cost) = $this->queue->bottom();
                $cost = $cost ? $cost : $this->config['cost'];
                if ($this->config['tokens'] >= 0) {
                    $this->config['tokens'] -= $cost;
                    $future->resolve(null);
                    $this->queue->dequeue();
                    # context switch?
                    # yield 0;
                    if ($this->queue->count() === 0) {
                        $this->running = false;
                    }
                } else {
                    $time = $this->config['delay'];
                    $sleep = new Promise(function ($resolve) use ($time) {
                        Loop::addTimer($time, function () use ($resolve) {
                            $resolve(null);
                        });
                    });
                    Async\await($sleep);
                    $now = microtime(true) * 1000;
                    $elapsed = $now - $last_timestamp;
                    $last_timestamp = $now;
                    $this->config['tokens'] = min($this->config['tokens'] + ($elapsed * $this->config['refillRate']), $this->config['capacity']);
                }
            }
        }) ();
    }


    public function __invoke($cost = null) {
        $future = new Deferred();
        if ($this->queue->count() > $this->config['maxCapacity']) {
            throw new \RuntimeException('throttle queue is over maxCapacity (' . strval($this->config['maxCapacity']) . '), see https://docs.ccxt.com/#/README?id=maximum-requests-capacity');
        }
        $this->queue->enqueue(array($future, $cost));
        if (!$this->running) {
            Loop::futureTick(array($this, 'loop'));
            $this->running = true;
        }
        return $future->promise();
    }
}

```

## High-Level Overview

This is a PHP file located at `php/async/Throttler.php`.

**Classes defined**: Throttler

**Functions defined**: loop, __invoke, __construct



## Detailed Walkthrough

### Code Structure

- Total lines: 74
- Code lines: 64
- Comment lines: 2
- Blank lines: 8

### Main Components

**Classes** (1):
- `Throttler`

**Functions** (3):
- `__construct()`
- `__invoke()`
- `loop()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/async/Throttler.php
```

