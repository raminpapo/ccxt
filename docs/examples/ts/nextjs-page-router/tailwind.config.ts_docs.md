# Documentation: examples/ts/nextjs-page-router/tailwind.config.ts

## File Metadata

- **Path**: `examples/ts/nextjs-page-router/tailwind.config.ts`
- **Size**: 507 bytes
- **Lines**: 21
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import type { Config } from 'tailwindcss'

const config: Config = {
  content: [
    './src/pages/**/*.{js,ts,jsx,tsx,mdx}',
    './src/components/**/*.{js,ts,jsx,tsx,mdx}',
    './src/app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      backgroundImage: {
        'gradient-radial': 'radial-gradient(var(--tw-gradient-stops))',
        'gradient-conic':
          'conic-gradient(from 180deg at 50% 50%, var(--tw-gradient-stops))',
      },
    },
  },
  plugins: [],
}
export default config

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/nextjs-page-router/tailwind.config.ts`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 19
- Comment lines: 0
- Blank lines: 2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `tailwindcss` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node examples/ts/nextjs-page-router/tailwind.config.ts
```

