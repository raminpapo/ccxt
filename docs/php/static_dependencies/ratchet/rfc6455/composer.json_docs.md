# Documentation: php/static_dependencies/ratchet/rfc6455/composer.json

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/composer.json`
- **Size**: 1,217 bytes
- **Lines**: 47
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "name": "ratchet/rfc6455",
    "type": "library",
    "description": "RFC6455 WebSocket protocol handler",
    "keywords": ["WebSockets", "websocket", "RFC6455"],
    "homepage": "http://socketo.me",
    "license": "MIT",
    "authors": [
        {
            "name": "Chris Boden"
          , "email": "cboden@gmail.com"
          , "role": "Developer"
        },
        {
            "name": "Matt Bonneau",
            "role": "Developer"
        }
    ],
    "support": {
        "issues": "https://github.com/ratchetphp/RFC6455/issues",
        "chat": "https://gitter.im/reactphp/reactphp"
    },
    "autoload": {
        "psr-4": {
            "Ratchet\\RFC6455\\": "src"
        }
    },
    "require": {
        "php": ">=5.4.2",
        "guzzlehttp/psr7": "^2 || ^1.7"
    },
    "require-dev": {
        "phpunit/phpunit": "^5.7",
        "react/socket": "^1.3"
    },
    "scripts": {
        "abtest-client": "ABTEST=client && sh tests/ab/run_ab_tests.sh",
        "abtest-server": "ABTEST=server && sh tests/ab/run_ab_tests.sh",
        "phpunit": "phpunit --colors=always",
        "test": [
            "@abtest-client",
            "@abtest-server",
            "@phpunit"
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `php/static_dependencies/ratchet/rfc6455/composer.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 46
- Comment lines: 0
- Blank lines: 1

### Main Components

**Constants** (1):
- `ABTEST`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `ABTEST=client && sh tests/ab/run_ab_tests.sh` (referenced)
- `ABTEST=server && sh tests/ab/run_ab_tests.sh` (referenced)
- `http://socketo.me` (referenced)



## Testing & Execution

**To execute this JSON file:**

