# Documentation: js/src/static_dependencies/jsencrypt/lib/asn1js/asn1.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/jsencrypt/lib/asn1js/asn1.d.ts`
- **Size**: 1,801 bytes
- **Lines**: 52
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Int10 } from "./int10.js";
export declare class Stream {
    constructor(enc: Stream | number[], pos?: number);
    private enc;
    pos: number;
    get(pos?: number): number;
    hexDigits: string;
    hexByte(b: number): string;
    hexDump(start: number, end: number, raw: boolean): string;
    isASCII(start: number, end: number): boolean;
    parseStringISO(start: number, end: number): string;
    parseStringUTF(start: number, end: number): string;
    parseStringBMP(start: number, end: number): string;
    parseTime(start: number, end: number, shortYear: boolean): string;
    parseInteger(start: number, end: number): string | 0 | -1;
    parseBitString(start: number, end: number, maxLength: number): string;
    parseOctetString(start: number, end: number, maxLength: number): string;
    parseOID(start: number, end: number, maxLength: number): string;
}
export declare class ASN1 {
    constructor(stream: Stream, header: number, length: number, tag: ASN1Tag, sub: ASN1[]);
    private stream;
    private header;
    private length;
    private tag;
    sub: ASN1[];
    typeName(): string;
    content(maxLength: number): string | 0 | -1;
    toString(): string;
    toPrettyString(indent: string): string;
    posStart(): number;
    posContent(): number;
    posEnd(): number;
    toHexString(): string;
    static decodeLength(stream: Stream): number;
    /**
     * Retrieve the hexadecimal value (as a string) of the current ASN.1 element
     * @returns {string}
     * @public
     */
    getHexStringValue(): string;
    static decode(str: Stream | number[]): ASN1;
}
export declare class ASN1Tag {
    constructor(stream: Stream);
    tagClass: number;
    tagConstructed: boolean;
    tagNumber: number | Int10;
    isUniversal(): boolean;
    isEOC(): boolean;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/jsencrypt/lib/asn1js/asn1.d.ts`.

**Classes defined**: ASN1, Stream, ASN1Tag

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 51
- Comment lines: 5
- Blank lines: -4

### Main Components

**Classes** (3):
- `ASN1`
- `ASN1Tag`
- `Stream`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./int10.js` (imported)
- `./int10.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/jsencrypt/lib/asn1js/asn1.d.ts
```

