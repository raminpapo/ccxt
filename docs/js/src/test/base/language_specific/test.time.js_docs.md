# Documentation: js/src/test/base/language_specific/test.time.js

## File Metadata

- **Path**: `js/src/test/base/language_specific/test.time.js`
- **Size**: 2,594 bytes
- **Lines**: 47
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
"use strict";
// ----------------------------------------------------------------------------
// import { strictEqual,  equal } from 'assert'
// import { setTimeout_safe, timeout, now, isWindows } from '../../../../ccxt.js'
//       , approxEqual = (a, b) => equal (true, Math.abs (a - b) <= 20)
//       , rejectsWith = (msg, x) =>
//         x.then (() => { throw new Error ('not rejected!') })
//          .catch ((e) => { equal (e.message, msg) })
// these tests break Travis 80% of the time
// TODO: make a more robust test that is not failing on certain machines under certain conditions
// ----------------------------------------------------------------------------
// it ('setTimeout_safe is working', (done) => {
//     if (isWindows) {
//         // temporarily skip this test with appveyor
//         // todo: refix timer functions for windows properly
//         done ()
//     } else {
//         const start = now ()
//         const calls = []
//         const brokenSetTimeout = (done, ms) => {
//             calls.push ({ when: now () - start, ms_asked: ms })
//             return setTimeout (done, 100) // simulates a defect setTimeout implementation that sleeps wrong time (100ms always in this test)
//         }
//         // ask to sleep 250ms
//         setTimeout_safe (() => {
//             approxEqual (calls[0].ms_asked, 250)
//             approxEqual (calls[1].ms_asked, 150)
//             approxEqual (calls[2].ms_asked, 50)
//             done ()
//         }, 250, brokenSetTimeout)
//     }
// })
// ----------------------------------------------------------------------------
// it ('setTimeout_safe canceling is working', (done) => {
//     const brokenSetTimeout = (done, ms) => setTimeout (done, 100) // simulates a defect setTimeout implementation that sleeps wrong time (100ms always in this test)
//     const clear = setTimeout_safe (() => { throw new Error ('shouldnt happen!') }, 250, brokenSetTimeout)
//     setTimeout (() => { clear () }, 200)
//     setTimeout (() => { done () }, 400)
// })
// ----------------------------------------------------------------------------
// it ('timeout() is working', async () => {
//     equal ('foo', await timeout (200, new Promise (resolve => setTimeout (() => resolve ('foo'), 100))))
//     await rejectsWith ('foo',       timeout (100, Promise.reject (new Error ('foo'))))
//     await rejectsWith ('timed out', timeout (100, new Promise ((resolve, reject) => setTimeout (() => reject (new Error ('foo')), 200))))
// })
// ----------------------------------------------------------------------------

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/language_specific/test.time.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 1
- Comment lines: 45
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/base/language_specific/test.time.js
```

