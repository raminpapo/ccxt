# Documentation: js/src/base/functions/string.js

## File Metadata

- **Path**: `js/src/base/functions/string.js`
- **Size**: 1,784 bytes
- **Lines**: 39
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// ----------------------------------------------------------------------------
// unCamelCase has to work with the following edge cases
//
//     parseOHLCVs               > parse_ohlcvs
//     safeString2               > safe_string_2
//     safeStringN               > safe_string_n
//     convertOHLCVToTradingView > convert_ohlcv_to_trading_view
//     fetchL2OrderBook          > fetch_l2_order_book
//     stringToBase64            > string_to_base64
//     base64ToString            > base64_to_string
//     parseHTTPResponse         > parse_http_response
//     hasFetchOHLCV             > has_fetch_ohlcv
//
// @ts-nocheck
const unCamelCase = (s) => {
    const exceptions = {
        'fetchOHLCVWs': 'fetch_ohlcv_ws', // ws = websocket
    };
    if (exceptions[s]) {
        return exceptions[s];
    }
    return s.match(/[A-Z]/) ? s.replace(/[a-z0-9][A-Z]/g, (x) => x[0] + '_' + x[1]).replace(/[A-Z0-9][A-Z0-9][a-z][^$]/g, (x) => x[0] + '_' + x[1] + x[2] + x[3]).replace(/[a-z][0-9]$/g, (x) => x[0] + '_' + x[1]).toLowerCase() : s;
};
const capitalize = (s) => {
    return s.length ? (s.charAt(0).toUpperCase() + s.slice(1)) : s;
};
const strip = (s) => s.replace(/^\s+|\s+$/g, '');
// ----------------------------------------------------------------------------
const uuid = (a) => {
    return a ? (a ^ Math.random() * 16 >> a / 4).toString(16) : ([1e7] + -1e3 + -4e3 + -8e3 + -1e11).replace(/[018]/g, uuid);
};
const uuid16 = (a) => {
    return a ? (a ^ Math.random() * 16 >> a / 4).toString(16) : ([1e5] + 1e2 + 4e2 + 8e3).replace(/[018]/g, uuid16);
};
const uuid22 = (a) => {
    return a ? (a ^ Math.random() * 16 >> a / 4).toString(16) : ([1e7] + 1e3 + 4e3 + 8e5).replace(/[018]/g, uuid22);
};
export { uuid, uuid16, uuid22, unCamelCase, capitalize, strip, };

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/functions/string.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 23
- Comment lines: 15
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/functions/string.js
```

