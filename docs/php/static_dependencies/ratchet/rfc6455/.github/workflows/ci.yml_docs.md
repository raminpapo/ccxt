# Documentation: php/static_dependencies/ratchet/rfc6455/.github/workflows/ci.yml

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/.github/workflows/ci.yml`
- **Size**: 949 bytes
- **Lines**: 44
- **Type**: YAML
- **Extension**: .yml


## Original Source Code

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  PHPUnit:
    name: PHPUnit (PHP ${{ matrix.php }})(${{ matrix.env }})
    runs-on: ubuntu-20.04
    strategy:
      matrix:
        env:
          - client
          - server
        php:
          - 7.4
          - 7.3
          - 7.2
          - 7.1
          - 7.0
          - 5.6
    steps:
      - uses: actions/checkout@v2
      - name: Setup PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: ${{ matrix.php }}
          coverage: xdebug
      - run: docker pull crossbario/autobahn-testsuite
      - run: composer install

      - run: sh tests/ab/run_ab_tests.sh
        env:
            ABTEST: ${{ matrix.env }}
            SKIP_DEFLATE: _skip_deflate
        if: ${{ matrix.php <= 5.6 }}

      - run: sh tests/ab/run_ab_tests.sh
        env:
            ABTEST: ${{ matrix.env }}
        if: ${{ matrix.php >= 7.0 }}
      - run: vendor/bin/phpunit --verbose

```

## High-Level Overview

This is a YAML file located at `php/static_dependencies/ratchet/rfc6455/.github/workflows/ci.yml`.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 39
- Comment lines: 0
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this YAML file:**

