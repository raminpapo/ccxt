# Documentation: php/pro/Future.php

## File Metadata

- **Path**: `php/pro/Future.php`
- **Size**: 2,315 bytes
- **Lines**: 75
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt\pro;

use React\EventLoop\Loop;
use React\Promise\Deferred;
use React\Promise\PromiseInterface;
use RuntimeException;

use function React\Promise\race;

class Future implements PromiseInterface {
    private Deferred $deferred;
    private bool $hasListeners = false;

    // implements PromiseInterface lets it be awaitable
    public function __construct() {
        $this->deferred = new Deferred();
    }

    public function then(?callable $onFulfilled = null, ?callable $onRejected = null): PromiseInterface {
        $this->hasListeners = true;
        return $this->deferred->promise()->then($onFulfilled, $onRejected);
    }

    public function resolve($value = null) {
        // from the docs
        // Unlike timers, tick callbacks are guaranteed to be executed in the order they are enqueued.
        Loop::futureTick(function () use ($value) {
            $this->deferred->resolve($value);
        });
    }

    public function reject($reason = null) {
        Loop::futureTick(function () use ($reason) {
            $this->deferred->reject($reason);
        });
    }

    public function catch(callable $onRejected): PromiseInterface {
        $this->hasListeners = true;
        return $this->deferred->promise()->catch($onRejected);
    }

    public function finally(callable $onFulfilledOrRejected): PromiseInterface {
        $this->hasListeners = true;
        return $this->deferred->promise()->finally($onFulfilledOrRejected);
    }

    public function cancel(): void {
        if ($this->hasListeners) {
            $this->deferred->reject(new RuntimeException('Promise has been canceled'));
        } else {
            $this->deferred->promise()->cancel();
        }
    }

    public function otherwise(callable $onRejected): PromiseInterface {
        // deprecated
        return $this->deferred->promise()->otherwise($onRejected);
    }

    public function always(callable $onFulfilledOrRejected): PromiseInterface {
        // deprecated
        return $this->deferred->promise()->always($onFulfilledOrRejected);
    }

    public static function race(array $futures): Future {
        $future = new Future();
        $promise = race($futures);
        $promise->then(array($future, 'resolve'), array($future, 'reject'));
        return $future;
    }
};

```

## High-Level Overview

This is a PHP file located at `php/pro/Future.php`.

**Classes defined**: Future

**Functions defined**: then, otherwise, cancel, resolve, always, __construct, React, finally, reject, catch



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 55
- Comment lines: 5
- Blank lines: 15

### Main Components

**Functions** (11):
- `React()`
- `__construct()`
- `always()`
- `cancel()`
- `catch()`
- `finally()`
- `otherwise()`
- `race()`
- `reject()`
- `resolve()`
- `then()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/pro/Future.php
```

