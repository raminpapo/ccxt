# Documentation: php/static_dependencies/ratchet/pawl/.github/workflows/ci.yml

## File Metadata

- **Path**: `php/static_dependencies/ratchet/pawl/.github/workflows/ci.yml`
- **Size**: 996 bytes
- **Lines**: 46
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
    name: PHPUnit (PHP ${{ matrix.php }})
    runs-on: ubuntu-20.04
    strategy:
      matrix:
        php:
          - 8.0
          - 7.4
          - 7.3
          - 7.2
          - 7.1
          - 7.0
          - 5.6
          - 5.5
          - 5.4
    steps:
      - uses: actions/checkout@v2
      - uses: shivammathur/setup-php@v2
        with:
          php-version: ${{ matrix.php }}
          coverage: xdebug
      - run: composer install
      - run: vendor/bin/phpunit --coverage-text
        if: ${{ matrix.php >= 7.3 }}
      - run: vendor/bin/phpunit --coverage-text -c phpunit.xml.legacy
        if: ${{ matrix.php < 7.3 }}

  PHPUnit-hhvm:
    name: PHPUnit (HHVM)
    runs-on: ubuntu-18.04
    continue-on-error: true
    steps:
      - uses: actions/checkout@v2
      - uses: azjezz/setup-hhvm@v1
        with:
          version: lts-3.30
      - run: hhvm $(which composer) install
      - run: hhvm vendor/bin/phpunit

```

## High-Level Overview

This is a YAML file located at `php/static_dependencies/ratchet/pawl/.github/workflows/ci.yml`.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 42
- Comment lines: 0
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this YAML file:**

