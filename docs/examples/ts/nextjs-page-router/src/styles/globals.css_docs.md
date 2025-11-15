# Documentation: examples/ts/nextjs-page-router/src/styles/globals.css

## File Metadata

- **Path**: `examples/ts/nextjs-page-router/src/styles/globals.css`
- **Size**: 538 bytes
- **Lines**: 28
- **Type**: CSS
- **Extension**: .css


## Original Source Code

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

:root {
  --foreground-rgb: 0, 0, 0;
  --background-start-rgb: 214, 219, 220;
  --background-end-rgb: 255, 255, 255;
}

@media (prefers-color-scheme: dark) {
  :root {
    --foreground-rgb: 255, 255, 255;
    --background-start-rgb: 0, 0, 0;
    --background-end-rgb: 0, 0, 0;
  }
}

body {
  color: rgb(var(--foreground-rgb));
  background: linear-gradient(
      to bottom,
      transparent,
      rgb(var(--background-end-rgb))
    )
    rgb(var(--background-start-rgb));
}

```

## High-Level Overview

This is a CSS file located at `examples/ts/nextjs-page-router/src/styles/globals.css`.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 24
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

**To execute this CSS file:**

