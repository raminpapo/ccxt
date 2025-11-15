# Documentation: php/static_dependencies/ratchet/rfc6455/tests/AbResultsTest.php

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/tests/AbResultsTest.php`
- **Size**: 1,052 bytes
- **Lines**: 33
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Ratchet\RFC6455\Test;
use PHPUnit\Framework\TestCase;

class AbResultsTest extends TestCase {
    private function verifyAutobahnResults($fileName) {
        if (!file_exists($fileName)) {
            return $this->markTestSkipped('Autobahn TestSuite results not found');
        }

        $resultsJson = file_get_contents($fileName);
        $results = json_decode($resultsJson);
        $agentName = array_keys(get_object_vars($results))[0];

        foreach ($results->$agentName as $name => $result) {
            if ($result->behavior === "INFORMATIONAL") {
                continue;
            }

            $this->assertTrue(in_array($result->behavior, ["OK", "NON-STRICT"]), "Autobahn test case " . $name . " in " . $fileName);
        }
    }

    public function testAutobahnClientResults() {
        $this->verifyAutobahnResults(__DIR__ . '/ab/reports/clients/index.json');
    }

    public function testAutobahnServerResults() {
        $this->verifyAutobahnResults(__DIR__ . '/ab/reports/servers/index.json');
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/ratchet/rfc6455/tests/AbResultsTest.php`.

**Classes defined**: AbResultsTest

**Functions defined**: testAutobahnClientResults, verifyAutobahnResults, testAutobahnServerResults



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 25
- Comment lines: 0
- Blank lines: 8

### Main Components

**Functions** (3):
- `testAutobahnClientResults()`
- `testAutobahnServerResults()`
- `verifyAutobahnResults()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ab/reports/clients/index.json` (referenced)
- `/ab/reports/servers/index.json` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
