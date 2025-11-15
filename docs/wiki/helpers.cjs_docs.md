# Documentation: wiki/helpers.cjs

## File Metadata

- **Path**: `wiki/helpers.cjs`
- **Size**: 1,527 bytes
- **Lines**: 48
- **Type**: Unknown
- **Extension**: .cjs


## Original Source Code

```
var arrayify = require('array-back')

const cache = {}

exports.getFragment = function (func) {
    // this function allows for links with the same name
    // and caches the link so we can regenerate the same id
    const { id, name, exchange } = func
    const selector = exchange ? exchange + name : name
    const lower = selector.toLowerCase ()
    if (exchange && !(id in cache)) {
        cache[lower] = cache[lower] || 0
        cache[id] = cache[lower]++
    }
    const part = (cache[id] >= 1) ? '-' + cache[id] : ''
    return lower + part
}

exports.cleanNames = function (names) {
    if (!names) return []
    return names.map (name => name.replace (/Array./g, 'Array'))
}

// this method is copied from dmd except for the option params handling
function methodSig () {
    const args = arrayify(this.params).filter(function (param) {
      return param.name && !/\./.test(param.name)
    })
    function firstOptionalIndex (params) {
        let i = 0;
        for (; i < params.length && !(params[i].optional); i++);
        return i
    }
    const names = args.map (arg => arg.name)
    if (args.length) {
        const firstOptional = firstOptionalIndex (args)
        if ((firstOptional > 0) && (args.length > 1)) {
            names[firstOptional - 1] = names[firstOptional - 1] + '['
        } else {
            names[firstOptional] = '[' + names[firstOptional]
        }
        names[names.length - 1] = names[names.length - 1] + ']'
    }
    return names.join (', ')
}

exports.methodSig = methodSig

```

## High-Level Overview

This is a Unknown file located at `wiki/helpers.cjs`.

**Functions defined**: methodSig, firstOptionalIndex, allows

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 39
- Comment lines: 3
- Blank lines: 6

### Main Components

**Functions** (3):
- `allows()`
- `firstOptionalIndex()`
- `methodSig()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Unknown file:**

