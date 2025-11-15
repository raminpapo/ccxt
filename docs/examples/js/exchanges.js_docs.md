# Documentation: examples/js/exchanges.js

## File Metadata

- **Path**: `examples/js/exchanges.js`
- **Size**: 1,194 bytes
- **Lines**: 41
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import countries from '../../build/countries.js';
import asTable from 'as-table';
import ololog from 'ololog'
import ansicolor from 'ansicolor';
const log = ololog.configure ({ locate: false })

ansicolor.nice

process.on ('uncaughtException',  e => { log.bright.red.error (e); process.exit (1) })
process.on ('unhandledRejection', e => { log.bright.red.error (e); process.exit (1) })

let exchanges = {}

ccxt.exchanges.forEach (id => { exchanges[id] = new (ccxt)[id] () })

log ('The ccxt library supports', (ccxt.exchanges.length.toString ()).green, 'exchanges:')

var countryName = function (code) {
    return ((countries[code] !== undefined) ? countries[code] : code)
}

log (asTable.configure ({ delimiter: ' | ' }) (Object.values (exchanges).map (exchange => {

    let countries = Array.isArray (exchange.countries) ?
        exchange.countries.map (countryName).join (', ') :
        countryName (exchange.countries)

    let website = Array.isArray (exchange.urls.www) ? exchange.urls.www[0] : exchange.urls.www

    return {
        id: exchange.id,
        name: exchange.name,
        url: website,
        countries: countries,
    }

})))

```

## High-Level Overview

This is a JavaScript file located at `examples/js/exchanges.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 27
- Comment lines: 0
- Blank lines: 14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `ansicolor` (imported)
- `../../build/countries.js` (imported)
- `ololog` (imported)
- `../../js/ccxt.js` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)
- `../../build/countries.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/exchanges.js
```

