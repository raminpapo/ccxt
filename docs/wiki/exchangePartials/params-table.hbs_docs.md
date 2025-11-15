# Documentation: wiki/exchangePartials/params-table.hbs

## File Metadata

- **Path**: `wiki/exchangePartials/params-table.hbs`
- **Size**: 460 bytes
- **Lines**: 13
- **Type**: Unknown
- **Extension**: .hbs


## Original Source Code

```
{{#if params}}

{{tableHead params "name|Param" "type|Type" "optional|Required" "description|Description" ~}}

{{#tableRow params "name" "type" "optional" "description" ~}}
| {{#if @col1}}{{name}} | {{/if~}}
{{#if @col2}}{{>linked-type-list types=(cleanNames type.names) delimiter=", " }} | {{/if~}}
{{#if @col3}}{{#unless optional}}Yes{{else}}No{{/unless}} | {{/if~}}
{{#if @col4}}{{{stripNewlines (inlineLinks description)}}} |{{/if}}
{{/tableRow}}

{{/if}}

```

## High-Level Overview

This is a Unknown file located at `wiki/exchangePartials/params-table.hbs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 9
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

**To execute this Unknown file:**

