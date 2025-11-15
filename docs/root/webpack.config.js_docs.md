# Documentation: webpack.config.js

## File Metadata

- **Path**: `webpack.config.js`
- **Size**: 1,386 bytes
- **Lines**: 56
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import path from 'path';
import url from 'url';
import TerserPlugin from "terser-webpack-plugin";
import webpack from 'webpack';

const cwd = url.fileURLToPath (import.meta.url);
const outputDirectory = path.normalize (path.join (path.dirname (cwd), 'dist'))

export default {
  entry : './ts/ccxt.ts',
  output: {
    path: outputDirectory,
    filename: 'ccxt.browser.js',
    library: {
      type: 'self', // we are targeting the browser (including webworkers)
      name: 'ccxt',
    },
    chunkFormat: 'array-push',
    chunkLoading: 'jsonp',
  },
  cache: {
    type: 'filesystem',
  },
  module: {
    rules: [{
      test: /\.ts$/,
      use: 'ts-loader',
      exclude: [ /node_modules/ ],
      sideEffects: false,
    }],
  },
  resolve: {
    extensions: [ '.ts' ],
    // this line is needed because we use import xxx.js in ccxt
    extensionAlias: {
     '.js': [ '.js', '.ts' ],
    },
  },
  mode: 'production',
  target: 'web',
  optimization: {
    minimize: false,
    minimizer: [new TerserPlugin ({ extractComments: false })],
    usedExports: true, // these two lines line turns on tree shaking
    concatenateModules: false,
    splitChunks: false,
  },
  performance: {
    hints: false,
  },
  plugins: [
    new webpack.IgnorePlugin({ resourceRegExp: /^protobufjs\/minimal(.js)?$/ }),
    new webpack.optimize.LimitChunkCountPlugin({ maxChunks: 1 }),
  ],
}

```

## High-Level Overview

This is a JavaScript file located at `webpack.config.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 52
- Comment lines: 1
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `url` (imported)
- `path` (imported)
- `terser-webpack-plugin` (imported)
- `webpack` (imported)
- `./ts/ccxt.ts` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node webpack.config.js
```

