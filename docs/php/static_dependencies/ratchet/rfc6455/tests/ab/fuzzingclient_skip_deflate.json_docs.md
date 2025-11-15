# Documentation: php/static_dependencies/ratchet/rfc6455/tests/ab/fuzzingclient_skip_deflate.json

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/tests/ab/fuzzingclient_skip_deflate.json`
- **Size**: 318 bytes
- **Lines**: 15
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "options": {
        "failByDrop": false
    }
  , "outdir": "/reports/servers"
  , "servers": [{
        "agent": "RatchetRFC/0.3"
      , "url": "ws://host.ratchet.internal:9001"
      , "options": {"version": 18}
    }]
  , "cases": ["*"]
  , "exclude-cases": ["12.*", "13.*"]
  , "exclude-agent-cases": {}
}

```

## High-Level Overview

This is a JSON file located at `php/static_dependencies/ratchet/rfc6455/tests/ab/fuzzingclient_skip_deflate.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 14
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
