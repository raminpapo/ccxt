# Documentation: php/static_dependencies/ratchet/pawl/composer.json

## File Metadata

- **Path**: `php/static_dependencies/ratchet/pawl/composer.json`
- **Size**: 657 bytes
- **Lines**: 26
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "name": "ratchet/pawl"
  , "description": "Asynchronous WebSocket client"
  , "keywords": ["WebSocket", "client", "Ratchet", "async", "websocket client"]
  , "license": "MIT"
  , "autoload": {
        "psr-4": {
            "Ratchet\\Client\\": "src"
        }
      , "files": ["src/functions_include.php"]
    }
  , "require": {
        "php": ">=5.4"
      , "evenement/evenement": "^3.0 || ^2.0"
      , "guzzlehttp/psr7": "^2.0 || ^1.7"
      , "ratchet/rfc6455": "^0.3.1"
      , "react/socket": "^1.9"
    }
  , "require-dev": {
        "phpunit/phpunit": "^9.3 || ^5.7 || ^4.8"
    }
  , "suggest": {
        "reactivex/rxphp": "~2.0"
    }
}

```

## High-Level Overview

This is a JSON file located at `php/static_dependencies/ratchet/pawl/composer.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 25
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

