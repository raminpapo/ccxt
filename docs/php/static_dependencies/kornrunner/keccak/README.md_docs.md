# Documentation: php/static_dependencies/kornrunner/keccak/README.md

## File Metadata

- **Path**: `php/static_dependencies/kornrunner/keccak/README.md`
- **Size**: 1,113 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
# php-keccak [![Build Status](https://travis-ci.org/kornrunner/php-keccak.svg?branch=master)](https://travis-ci.org/kornrunner/php-keccak)  [![Coverage Status](https://coveralls.io/repos/github/kornrunner/php-keccak/badge.svg?branch=master)](https://coveralls.io/github/kornrunner/php-keccak?branch=master)
Pure PHP implementation of Keccak (SHA-3)

## Usage

```php
<?php

use kornrunner\Keccak;

Keccak::hash('', 224);
// f71837502ba8e10837bdd8d365adb85591895602fc552b48b7390abd

Keccak::hash('', 256);
// c5d2460186f7233c927e7db2dcc703c0e500b653ca82273b7bfad8045d85a470

Keccak::hash('', 384);
// 2c23146a63a29acf99e73b88f8c24eaa7dc60aa771780ccc006afbfa8fe2479b2dd2b21362337441ac12b515911957ff

Keccak::hash('', 512);
// 0eab42de4c3ceb9235fc91acffe746b29c29a8c366b7c60e4e67c466f36a4304c00fa9caf9d87976ba469bcbe06713b435f091ef2769fb160cdab33d3670680e

Keccak::shake('', 128, 256);
// 7f9c2ba4e88f827d616045507605853ed73b8093f6efbc88eb1a6eacfa66ef26

Keccak::shake('', 256, 512);
// 46b9dd2b0ba88d13233b3feb743eeb243fcd52ea62b81b82b50c27646ed5762fd75dc4ddd8c0f200cb05019d67b592f6fc821c49479ab48640292eacb3b7c4be

```

## High-Level Overview

This is a Markdown file located at `php/static_dependencies/kornrunner/keccak/README.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 10
- Comment lines: 8
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

