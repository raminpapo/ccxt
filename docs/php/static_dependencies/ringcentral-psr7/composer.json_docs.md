# Documentation: php/static_dependencies/ringcentral-psr7/composer.json

## File Metadata

- **Path**: `php/static_dependencies/ringcentral-psr7/composer.json`
- **Size**: 823 bytes
- **Lines**: 36
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "name": "ringcentral/psr7",
    "type": "library",
    "description": "PSR-7 message implementation",
    "keywords": ["message", "stream", "http", "uri"],
    "license": "MIT",
    "authors": [
        {
            "name": "Michael Dowling",
            "email": "mtdowling@gmail.com",
            "homepage": "https://github.com/mtdowling"
        }
    ],
    "require": {
        "php": ">=5.3",
        "psr/http-message": "~1.0"
    },
    "require-dev": {
        "phpunit/phpunit": "~4.0"
    },
    "provide": {
        "psr/http-message-implementation": "1.0"
    },
    "autoload": {
        "psr-4": {
            "RingCentral\\Psr7\\": "src/"
        },
        "files": ["src/functions_include.php"]
    },
    "extra": {
        "branch-alias": {
            "dev-master": "1.0-dev"
        }
    }
}

```

## High-Level Overview

This is a JSON file located at `php/static_dependencies/ringcentral-psr7/composer.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 35
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `src/functions_include.php` (referenced)



## Testing & Execution

**To execute this JSON file:**

