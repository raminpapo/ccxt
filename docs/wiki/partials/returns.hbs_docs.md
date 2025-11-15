# Documentation: wiki/partials/returns.hbs

## File Metadata

- **Path**: `wiki/partials/returns.hbs`
- **Size**: 341 bytes
- **Lines**: 13
- **Type**: Unknown
- **Extension**: .hbs


## Original Source Code

```
{{#if returns}}
{{#if returns.[0].description~}}
**Returns**: {{#each returns~}}
  {{#if type~}}
  {{#if type.names}}{{>linked-type-list types=(cleanNames type.names) delimiter=" \| " ~}}{{/if}}
  {{~#if description}} - {{{inlineLinks description}}}{{/if~}}
  {{else~}}
  {{{inlineLinks description}~}}
  {{/if~}}
{{~/each}}

{{/if}}{{/if}}

```

## High-Level Overview

This is a Unknown file located at `wiki/partials/returns.hbs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 11
- Comment lines: 1
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Unknown file:**

