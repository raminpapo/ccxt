# Documentation: python/tox.ini

## File Metadata

- **Path**: `python/tox.ini`
- **Size**: 657 bytes
- **Lines**: 36
- **Type**: Unknown
- **Extension**: .ini


## Original Source Code

```
[tox]
envlist = py{37,38,39,310,311}
skipsdist = True
skip_missing_interpreters = False
ignore_basepython_conflict = True

[testenv]
basepython = python3
sitepackages = True
setenv =
    PYTHONPATH = {toxinidir}:{toxinidir}
deps =
    pip
    setuptools
    wheel
    aiohttp
    cryptography
    requests
    coincurve
commands =
    pip install -e .
    python ccxt/test/tests_init.py --idTests
    python ccxt/test/tests_init.py --sync --idTests

[testenv:qa]
allowlist_externals = ruff
changedir = {toxinidir}
commands = ruff ./ccxt/
deps = .[qa]

[testenv:type]
allowlist_externals = mypy
changedir = {toxinidir}
commands = mypy ./ccxt/
deps = .[type]

```

## High-Level Overview

This is a Unknown file located at `python/tox.ini`.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 32
- Comment lines: 0
- Blank lines: 4

### Main Components

**Constants** (1):
- `PYTHONPATH`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Unknown file:**

