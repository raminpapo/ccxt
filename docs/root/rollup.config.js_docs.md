# Documentation: rollup.config.js

## File Metadata

- **Path**: `rollup.config.js`
- **Size**: 1,273 bytes
- **Lines**: 45
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import commonjs from "@rollup/plugin-commonjs";
import json from "@rollup/plugin-json";
import execute from 'rollup-plugin-execute';
import nodeResolve from '@rollup/plugin-node-resolve'

export default [
  {
    preserveModules: true,
    context: 'globalThis',
    input: "./js/ccxt.js",
    output: [
      {
        dir: "./dist/cjs/",
        format: "cjs",
        exports: "named",
      }
    ],
    plugins: [
      nodeResolve({
        preferBuiltins: true,
        // node resolve generate dist/cjs/js directory 
        jail: '/src'
      }),
      json(),
      commonjs({
        transformMixedEsModules: true,
        dynamicRequireTargets: ["**/js/src/static_dependencies/**/*.cjs"],
      }),
      execute("echo '{ \"type\": \"commonjs\" }' > ./dist/cjs/package.json") // this is needed to make node treat files inside dist/cjs as CJS modules
    ],
    onwarn: ( warning, next ) => {
      if ( warning.message.indexOf('is implicitly using "default" export mode') > -1 ) return;
      next( warning );
    },
    external: [
      'socks-proxy-agent',
      // node resolve generate dist/cjs/js directory, treat ws, debug as external
      'ws',
      'debug',
      "http-proxy-agent",
      "https-proxy-agent",
      "protobufjs/minimal"
    ]
  }
];
```

## High-Level Overview

This is a JavaScript file located at `rollup.config.js`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 42
- Comment lines: 2
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `@rollup/plugin-node-resolve` (imported)
- `rollup-plugin-execute` (imported)
- `@rollup/plugin-json` (imported)
- `@rollup/plugin-commonjs` (imported)
- `./js/ccxt.js` (referenced)
- `**/js/src/static_dependencies/**/*.cjs` (referenced)
- ` > ./dist/cjs/package.json` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node rollup.config.js
```

