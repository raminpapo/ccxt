# Repository Documentation

## Overview

This directory contains comprehensive automatically-generated documentation for the entire repository.

## Structure

- **index.md** - Main entry point with links to all folders
- **keywords.md** - Global A-Z keyword index
- **comprehensive_book.md** - Complete documentation in book form
- **verification_report.md** - Processing report and validation
- **manifest.json** - Metadata and statistics

## Folder Organization

Each folder contains:
- `index.md` - List of files and subdirectories
- `doc.md` - Narrative context about the folder
- `sub.md` - Keyword index for the folder

## File Documentation

Each documented file has:
- `<filename>_docs.md` - Complete documentation
- `<filename>_kw.md` - Extracted keywords

## How to Use

1. Start with [index.md](index.md) for the overview
2. Browse [keywords.md](keywords.md) to find specific topics
3. Navigate folder indexes to explore specific areas
4. Read [comprehensive_book.md](comprehensive_book.md) for a linear walkthrough

## Resuming/Expanding

To regenerate or expand this documentation:

```bash
python3 repo_book_gen.py --source /path/to/repo --out ./docs --resume
```

Options:
- `--resume` - Skip already processed files
- `--max-file-chars N` - Limit characters read per file (default: 2,000,000)
- `--workers N` - Not implemented (single-threaded for now)

## Integrity

Check [verification_report.md](verification_report.md) for:
- Files successfully processed
- Files skipped (binary, large, ignored)
- Any errors encountered

All internal links use relative paths and were validated during generation.

---

**Generated**: See manifest.json for timestamp and statistics.
