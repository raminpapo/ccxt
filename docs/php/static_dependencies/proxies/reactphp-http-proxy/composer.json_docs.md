# Documentation: php/static_dependencies/proxies/reactphp-http-proxy/composer.json

## File Metadata

- **Path**: `php/static_dependencies/proxies/reactphp-http-proxy/composer.json`
- **Size**: 1,088 bytes
- **Lines**: 37
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "name": "clue/http-proxy-react",
    "description": "Async HTTP proxy connector, tunnel any TCP/IP-based protocol through an HTTP CONNECT proxy server, built on top of ReactPHP",
    "keywords": ["HTTP", "CONNECT", "proxy", "ReactPHP", "async"],
    "homepage": "https://github.com/clue/reactphp-http-proxy",
    "license": "MIT",
    "authors": [
        {
            "name": "Christian Lück",
            "email": "christian@clue.engineering"
        }
    ],
    "require": {
        "php": ">=5.3",
        "react/promise": "^3.2 || ^2.1 || ^1.2.1",
        "react/socket": "^1.16",
        "ringcentral/psr7": "^1.2"
    },
    "require-dev": {
        "phpunit/phpunit": "^9.6 || ^5.7 || ^4.8.36",
        "react/async": "^4.3 || ^3 || ^2",
        "react/event-loop": "^1.2",
        "react/http": "^1.11",
        "react/promise-timer": "^1.11"
    },
    "autoload": {
        "psr-4": { 
            "Clue\\React\\HttpProxy\\": "src/" 
        }
    },
    "autoload-dev": {
        "psr-4": { 
            "Clue\\Tests\\React\\HttpProxy\\": "tests/" 
        }
    }
}

```

## High-Level Overview

This is a JSON file located at `php/static_dependencies/proxies/reactphp-http-proxy/composer.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 36
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

**To execute this JSON file:**

