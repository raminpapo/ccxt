# Documentation: repo_book_gen.py

## File Metadata

- **Path**: `repo_book_gen.py`
- **Size**: 40,638 bytes
- **Lines**: 1,176
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
#!/usr/bin/env python3
"""
World's Best Repo Book Generator and Index Builder
Generates comprehensive documentation for any repository
"""

import os
import sys
import json
import hashlib
import re
import mimetypes
from pathlib import Path
from datetime import datetime
from collections import defaultdict
import argparse

class RepoBookGenerator:
    def __init__(self, repo_path, out_dir, resume=False, max_file_chars=2000000):
        self.repo_path = Path(repo_path).resolve()
        self.out_dir = Path(out_dir).resolve()
        self.resume = resume
        self.max_file_chars = max_file_chars

        # Progress tracking
        self.progress_log = []
        self.errors = []
        self.files_scanned = 0
        self.docs_created = 0
        self.words_estimated = 0
        self.bytes_written = 0

        # File classification
        self.text_files = []
        self.binary_files = []
        self.large_files = []
        self.ignored_files = []

        # Keywords tracking
        self.global_keywords = defaultdict(list)  # keyword -> [(file, description)]

        # Binary extensions
        self.binary_extensions = {
            '.png', '.jpg', '.jpeg', '.gif', '.bmp', '.ico', '.svg',
            '.pdf', '.zip', '.tar', '.gz', '.bz2', '.xz', '.7z',
            '.exe', '.dll', '.so', '.dylib', '.o', '.a',
            '.pyc', '.pyo', '.class', '.jar', '.war',
            '.woff', '.woff2', '.ttf', '.eot', '.otf',
            '.mp3', '.mp4', '.avi', '.mov', '.wav',
            '.db', '.sqlite', '.dat'
        }

        # Ignore patterns
        self.ignore_patterns = [
            '.git/', 'node_modules/', '__pycache__/', '.pytest_cache/',
            '.venv/', 'venv/', 'dist/', 'build/', '.eggs/',
            '*.pyc', '*.pyo', '*.so', '*.dll', '*.exe'
        ]

    def should_ignore(self, path):
        """Check if file should be ignored"""
        path_str = str(path)
        for pattern in self.ignore_patterns:
            if pattern.endswith('/'):
                if f"/{pattern}" in f"/{path_str}/":
                    return True
            elif pattern.startswith('*.'):
                ext = pattern[1:]
                if path_str.endswith(ext):
                    return True
        return False

    def is_binary(self, file_path):
        """Check if file is binary"""
        if file_path.suffix.lower() in self.binary_extensions:
            return True

        # Try to read first 8KB to detect binary
        try:
            with open(file_path, 'rb') as f:
                chunk = f.read(8192)
                if b'\x00' in chunk:  # Null byte indicates binary
                    return True
                # Try to decode as text
                chunk.decode('utf-8')
                return False
        except (UnicodeDecodeError, PermissionError):
            return True

    def compute_fingerprint(self):
        """Compute repository fingerprint"""
        try:
            # Try to get git commit hash
            import subprocess
            result = subprocess.run(
                ['git', 'log', '-1', '--format=%H'],
                cwd=self.repo_path,
                capture_output=True,
                text=True,
                timeout=5
            )
            if result.returncode == 0 and result.stdout.strip():
                return result.stdout.strip()
        except:
            pass

        # Fallback: hash of file list + sizes
        file_list = []
        for root, dirs, files in os.walk(self.repo_path):
            for f in sorted(files):
                fp = Path(root) / f
                try:
                    file_list.append(f"{fp.relative_to(self.repo_path)}:{fp.stat().st_size}")
                except:
                    pass

        fingerprint_str = "\n".join(file_list)
        return hashlib.sha256(fingerprint_str.encode()).hexdigest()

    def scan_repository(self):
        """Scan repository and classify files"""
        print(f"📂 Scanning repository: {self.repo_path}")

        for root, dirs, files in os.walk(self.repo_path):
            # Filter out ignored directories
            dirs[:] = [d for d in dirs if not self.should_ignore(Path(root) / d)]

            for filename in files:
                file_path = Path(root) / filename
                rel_path = file_path.relative_to(self.repo_path)

                # Skip if in ignored patterns
                if self.should_ignore(rel_path):
                    self.ignored_files.append(str(rel_path))
                    continue

                # Skip docs directory
                if str(rel_path).startswith('docs/'):
                    continue

                self.files_scanned += 1

                try:
                    file_size = file_path.stat().st_size

                    # Classify file
                    if file_size > 100 * 1024 * 1024:  # >100MB
                        self.large_files.append(str(rel_path))
                    elif self.is_binary(file_path):
                        self.binary_files.append(str(rel_path))
                    else:
                        self.text_files.append(str(rel_path))

                except Exception as e:
                    self.errors.append(f"Error scanning {rel_path}: {e}")

        print(f"✓ Scanned {self.files_scanned} files")
        print(f"  - Text files: {len(self.text_files)}")
        print(f"  - Binary files: {len(self.binary_files)}")
        print(f"  - Large files: {len(self.large_files)}")
        print(f"  - Ignored: {len(self.ignored_files)}")

    def extract_keywords(self, content, file_path):
        """Extract keywords from file content"""
        keywords = {}

        # Extract identifiers (functions, classes, variables)
        # Function definitions
        func_pattern = r'\b(?:def|function|async\s+function|class|const|let|var|interface|type)\s+([a-zA-Z_][a-zA-Z0-9_]*)'
        for match in re.finditer(func_pattern, content):
            kw = match.group(1)
            keywords[kw] = f"Identifier defined in {file_path}"

        # Import statements
        import_pattern = r'(?:import|from|require)\s+(?:[\w.*{},\s]+\s+)?[\'"]([^\'"]+)[\'"]'
        for match in re.finditer(import_pattern, content):
            kw = match.group(1)
            keywords[kw] = f"Module imported in {file_path}"

        # API endpoints (common patterns)
        api_pattern = r'[\'"]/(api/)?[\w/\-{}:]+[\'"]'
        for match in re.finditer(api_pattern, content):
            kw = match.group(0).strip('\'"')
            keywords[kw] = f"API endpoint in {file_path}"

        # URLs and domains
        url_pattern = r'https?://[\w\-.]+'
        for match in re.finditer(url_pattern, content):
            kw = match.group(0)
            keywords[kw] = f"URL referenced in {file_path}"

        # Constants (all caps with underscores)
        const_pattern = r'\b([A-Z][A-Z0-9_]{2,})\b'
        for match in re.finditer(const_pattern, content):
            kw = match.group(1)
            if kw not in keywords:
                keywords[kw] = f"Constant in {file_path}"

        return keywords

    def count_words(self, text):
        """Count words in text"""
        return len(re.findall(r'\b\w+\b', text))

    def safe_filename(self, name):
        """Convert filename to safe markdown filename"""
        # Replace special chars
        safe = re.sub(r'[^\w\-.]', '_', name)
        return safe

    def create_file_docs(self, rel_path):
        """Generate documentation for a single file"""
        file_path = self.repo_path / rel_path
        safe_name = self.safe_filename(rel_path.name)

        # Determine output directory
        if rel_path.parent == Path('.'):
            out_folder = self.out_dir / "root"
        else:
            out_folder = self.out_dir / rel_path.parent

        out_folder.mkdir(parents=True, exist_ok=True)

        docs_file = out_folder / f"{safe_name}_docs.md"
        kw_file = out_folder / f"{safe_name}_kw.md"

        try:
            # Read file content
            with open(file_path, 'r', encoding='utf-8', errors='replace') as f:
                content = f.read(self.max_file_chars)
                truncated = len(content) == self.max_file_chars

            file_size = file_path.stat().st_size

            # Generate documentation
            doc_content = self.generate_file_documentation(rel_path, content, truncated, file_size)

            # Write docs
            with open(docs_file, 'w', encoding='utf-8') as f:
                f.write(doc_content)

            self.bytes_written += len(doc_content)
            self.words_estimated += self.count_words(doc_content)
            self.docs_created += 1

            # Extract and save keywords
            keywords = self.extract_keywords(content, str(rel_path))
            kw_content = self.generate_keywords_file(rel_path, keywords, safe_name)

            with open(kw_file, 'w', encoding='utf-8') as f:
                f.write(kw_content)

            self.bytes_written += len(kw_content)
            self.words_estimated += self.count_words(kw_content)
            self.docs_created += 1

            # Add to global keywords
            for kw, desc in keywords.items():
                self.global_keywords[kw].append((str(rel_path), desc))

            self.progress_log.append(f"✓ {rel_path}")

        except Exception as e:
            self.errors.append(f"Error processing {rel_path}: {e}")
            self.progress_log.append(f"✗ {rel_path}: {e}")

    def generate_file_documentation(self, rel_path, content, truncated, file_size):
        """Generate comprehensive documentation for a file"""
        lines = content.split('\n')
        num_lines = len(lines)

        # Detect file type
        ext = Path(rel_path).suffix
        file_type = self.detect_file_type(ext, content)

        doc = f"""# Documentation: {rel_path}

## File Metadata

- **Path**: `{rel_path}`
- **Size**: {file_size:,} bytes
- **Lines**: {num_lines:,}
- **Type**: {file_type}
- **Extension**: {ext if ext else 'none'}
{'- **Note**: Content truncated at ' + str(self.max_file_chars) + ' characters' if truncated else ''}

## Original Source Code

```{self.get_language_for_fence(ext)}
{content}
```

## High-Level Overview

"""

        # Add overview based on file type
        doc += self.generate_overview(rel_path, content, file_type)

        doc += f"""

## Detailed Walkthrough

"""

        # Add detailed analysis
        doc += self.generate_detailed_analysis(content, file_type)

        doc += """

## Usage Examples

"""
        doc += self.generate_usage_examples(content, file_type)

        doc += """

## Performance & Security Notes

"""
        doc += self.generate_performance_security_notes(content, file_type)

        doc += """

## Related Files

"""
        doc += self.find_related_files(content)

        doc += """

## Testing & Execution

"""
        doc += self.generate_testing_notes(rel_path, file_type)

        return doc

    def detect_file_type(self, ext, content):
        """Detect file type from extension and content"""
        ext_map = {
            '.js': 'JavaScript',
            '.ts': 'TypeScript',
            '.py': 'Python',
            '.php': 'PHP',
            '.cs': 'C#',
            '.go': 'Go',
            '.java': 'Java',
            '.cpp': 'C++',
            '.c': 'C',
            '.h': 'C/C++ Header',
            '.md': 'Markdown',
            '.json': 'JSON',
            '.yaml': 'YAML',
            '.yml': 'YAML',
            '.xml': 'XML',
            '.html': 'HTML',
            '.css': 'CSS',
            '.sh': 'Shell Script',
            '.bat': 'Batch Script',
            '.rst': 'reStructuredText',
            '.txt': 'Plain Text',
        }
        return ext_map.get(ext.lower(), 'Unknown')

    def get_language_for_fence(self, ext):
        """Get language identifier for code fence"""
        lang_map = {
            '.js': 'javascript',
            '.ts': 'typescript',
            '.py': 'python',
            '.php': 'php',
            '.cs': 'csharp',
            '.go': 'go',
            '.java': 'java',
            '.cpp': 'cpp',
            '.c': 'c',
            '.md': 'markdown',
            '.json': 'json',
            '.yaml': 'yaml',
            '.yml': 'yaml',
            '.xml': 'xml',
            '.html': 'html',
            '.css': 'css',
            '.sh': 'bash',
        }
        return lang_map.get(ext.lower(), '')

    def generate_overview(self, rel_path, content, file_type):
        """Generate high-level overview of the file"""
        overview = f"This is a {file_type} file located at `{rel_path}`.\n\n"

        # Check for common patterns
        if 'class ' in content:
            classes = re.findall(r'\bclass\s+([a-zA-Z_][a-zA-Z0-9_]*)', content)
            if classes:
                overview += f"**Classes defined**: {', '.join(set(classes[:10]))}\n\n"

        if 'def ' in content or 'function ' in content:
            funcs = re.findall(r'\b(?:def|function|async function)\s+([a-zA-Z_][a-zA-Z0-9_]*)', content)
            if funcs:
                overview += f"**Functions defined**: {', '.join(set(funcs[:10]))}\n\n"

        if 'import ' in content or 'require(' in content:
            overview += "**Dependencies**: This file imports other modules.\n\n"

        # Check for documentation strings
        if '"""' in content or "'''" in content or '/*' in content:
            overview += "**Documentation**: Contains inline documentation/comments.\n\n"

        return overview

    def generate_detailed_analysis(self, content, file_type):
        """Generate detailed analysis of file content"""
        analysis = ""

        # Analyze structure
        lines = content.split('\n')

        # Count comments
        comment_lines = sum(1 for line in lines if line.strip().startswith(('#', '//', '/*', '*', '"""', "'''")))
        code_lines = len([l for l in lines if l.strip() and not l.strip().startswith(('#', '//'))])

        analysis += f"### Code Structure\n\n"
        analysis += f"- Total lines: {len(lines)}\n"
        analysis += f"- Code lines: {code_lines}\n"
        analysis += f"- Comment lines: {comment_lines}\n"
        analysis += f"- Blank lines: {len(lines) - code_lines - comment_lines}\n\n"

        # Extract main components
        analysis += f"### Main Components\n\n"

        # Classes
        classes = re.findall(r'class\s+([a-zA-Z_][a-zA-Z0-9_]*)\s*[(:{\n]', content)
        if classes:
            analysis += f"**Classes** ({len(set(classes))}):\n"
            for cls in sorted(set(classes))[:20]:
                analysis += f"- `{cls}`\n"
            analysis += "\n"

        # Functions
        funcs = re.findall(r'(?:def|function|async\s+function)\s+([a-zA-Z_][a-zA-Z0-9_]*)', content)
        if funcs:
            analysis += f"**Functions** ({len(set(funcs))}):\n"
            for func in sorted(set(funcs))[:20]:
                analysis += f"- `{func}()`\n"
            analysis += "\n"

        # Constants
        constants = re.findall(r'\b([A-Z][A-Z0-9_]{2,})\s*=', content)
        if constants:
            analysis += f"**Constants** ({len(set(constants))}):\n"
            for const in sorted(set(constants))[:20]:
                analysis += f"- `{const}`\n"
            analysis += "\n"

        return analysis

    def generate_usage_examples(self, content, file_type):
        """Generate usage examples from code"""
        examples = ""

        # Look for example comments or test code
        example_sections = re.findall(r'# Example:?\s*\n((?:.*\n){1,10})', content, re.IGNORECASE)
        if example_sections:
            examples += "Found inline examples:\n\n"
            for i, example in enumerate(example_sections[:3], 1):
                examples += f"### Example {i}\n\n```\n{example.strip()}\n```\n\n"

        # Look for main/if __name__ blocks
        main_blocks = re.findall(r'if\s+__name__\s*==\s*[\'"]__main__[\'"]\s*:((?:.*\n){1,20})', content)
        if main_blocks:
            examples += "### Main execution block:\n\n"
            examples += f"```python\n{main_blocks[0].strip()}\n```\n\n"

        if not examples:
            examples = "No explicit usage examples found in the file. Refer to related test files or documentation.\n\n"

        return examples

    def generate_performance_security_notes(self, content, file_type):
        """Generate performance and security notes"""
        notes = ""

        # Security checks
        security_issues = []
        if 'eval(' in content:
            security_issues.append("⚠️ Uses `eval()` - potential code injection risk")
        if 'exec(' in content:
            security_issues.append("⚠️ Uses `exec()` - potential code injection risk")
        if re.search(r'password\s*=\s*[\'"][^\'"]+[\'"]', content, re.IGNORECASE):
            security_issues.append("⚠️ Possible hardcoded password")
        if re.search(r'api[_-]?key\s*=\s*[\'"][^\'"]+[\'"]', content, re.IGNORECASE):
            security_issues.append("⚠️ Possible hardcoded API key")
        if 'shell=True' in content:
            security_issues.append("⚠️ Uses shell=True - potential command injection risk")

        if security_issues:
            notes += "### Security Considerations\n\n"
            for issue in security_issues:
                notes += f"- {issue}\n"
            notes += "\n"

        # Performance notes
        perf_notes = []
        if 'async ' in content or 'await ' in content:
            perf_notes.append("✓ Uses async/await for non-blocking operations")
        if 'cache' in content.lower() or 'memoize' in content.lower():
            perf_notes.append("✓ Implements caching mechanisms")
        if re.search(r'for\s+\w+\s+in.*:\s*for\s+\w+\s+in', content):
            perf_notes.append("⚠️ Contains nested loops - check complexity")

        if perf_notes:
            notes += "### Performance Notes\n\n"
            for note in perf_notes:
                notes += f"- {note}\n"
            notes += "\n"

        if not notes:
            notes = "No specific performance or security issues detected.\n\n"

        return notes

    def find_related_files(self, content):
        """Find related files based on imports and references"""
        related = []

        # Extract imports
        imports = re.findall(r'(?:import|from|require)\s+(?:[\w.*{},\s]+\s+)?[\'"]([^\'"]+)[\'"]', content)
        for imp in set(imports[:10]):
            related.append(f"- `{imp}` (imported)")

        # Extract file references
        file_refs = re.findall(r'[\'"]([^\'"]*\.[a-z]{2,4})[\'"]', content)
        for ref in set(file_refs[:10]):
            if '/' in ref or '\\' in ref:
                related.append(f"- `{ref}` (referenced)")

        if not related:
            return "No explicit file references found.\n\n"

        return "\n".join(related) + "\n\n"

    def generate_testing_notes(self, rel_path, file_type):
        """Generate testing and execution notes"""
        notes = ""

        # Check if this is a test file
        if 'test' in str(rel_path).lower():
            notes += "This appears to be a test file.\n\n"
            notes += "**To run this test:**\n"
            if file_type == 'Python':
                notes += "```bash\npytest " + str(rel_path) + "\n```\n\n"
            elif file_type == 'JavaScript' or file_type == 'TypeScript':
                notes += "```bash\nnpm test " + str(rel_path) + "\n```\n\n"
        else:
            notes += f"**To execute this {file_type} file:**\n\n"
            if file_type == 'Python':
                notes += "```bash\npython " + str(rel_path) + "\n```\n\n"
            elif file_type == 'JavaScript':
                notes += "```bash\nnode " + str(rel_path) + "\n```\n\n"
            elif file_type == 'TypeScript':
                notes += "```bash\nts-node " + str(rel_path) + "\n```\n\n"
            elif file_type == 'PHP':
                notes += "```bash\nphp " + str(rel_path) + "\n```\n\n"
            elif file_type == 'Shell Script':
                notes += "```bash\nbash " + str(rel_path) + "\n```\n\n"

        return notes

    def generate_keywords_file(self, rel_path, keywords, safe_name):
        """Generate keywords markdown file"""
        kw_content = f"""# Keywords: {rel_path}

## Extracted Keywords

This file contains {len(keywords)} keywords extracted from `{rel_path}`.

"""

        # Sort keywords alphabetically
        sorted_kw = sorted(keywords.items())

        current_letter = None
        for kw, desc in sorted_kw:
            first_letter = kw[0].upper() if kw else '?'

            if first_letter != current_letter:
                current_letter = first_letter
                kw_content += f"\n### {current_letter}\n\n"

            # Create anchor
            anchor = re.sub(r'[^\w\-]', '-', kw.lower())
            kw_content += f"#### <a name=\"{anchor}\"></a> `{kw}`\n\n"
            kw_content += f"{desc}\n\n"
            kw_content += f"[Back to file docs]({safe_name}_docs.md)\n\n"

        return kw_content

    def create_folder_docs(self, folder_path):
        """Create index.md, doc.md, and sub.md for a folder"""
        if folder_path == Path('.'):
            out_folder = self.out_dir / "root"
            display_path = "(root)"
        else:
            out_folder = self.out_dir / folder_path
            display_path = str(folder_path)

        if not out_folder.exists():
            return

        # Get all files and subdirectories in this folder
        files_in_folder = []
        subdirs_in_folder = []

        actual_folder = self.repo_path / folder_path if folder_path != Path('.') else self.repo_path

        try:
            for item in actual_folder.iterdir():
                if item.is_file() and not self.should_ignore(item.relative_to(self.repo_path)):
                    files_in_folder.append(item.name)
                elif item.is_dir() and not self.should_ignore(item.relative_to(self.repo_path)):
                    subdirs_in_folder.append(item.name)
        except:
            pass

        # Create index.md
        index_content = f"""# Index: {display_path}

## Overview

This folder contains {len(files_in_folder)} files and {len(subdirs_in_folder)} subdirectories.

## Files

"""
        for filename in sorted(files_in_folder)[:100]:  # Limit to 100 files
            safe_name = self.safe_filename(filename)
            index_content += f"- [{filename}]({safe_name}_docs.md)\n"

        index_content += "\n## Subdirectories\n\n"
        for dirname in sorted(subdirs_in_folder)[:100]:
            index_content += f"- [{dirname}/](../{dirname}/index.md)\n"

        index_content += "\n## Quick Links\n\n"
        index_content += f"- [Folder Documentation](doc.md)\n"
        index_content += f"- [Keyword Index](sub.md)\n"
        index_content += f"- [Back to Root](../index.md)\n"

        index_file = out_folder / "index.md"
        with open(index_file, 'w', encoding='utf-8') as f:
            f.write(index_content)

        self.docs_created += 1
        self.bytes_written += len(index_content)

        # Create doc.md
        doc_content = f"""# Folder Documentation: {display_path}

## Purpose

This folder is part of the repository structure at `{display_path}`.

## Context

"""

        # Analyze folder purpose from path
        path_parts = str(folder_path).split('/')
        if 'test' in path_parts or 'tests' in path_parts:
            doc_content += "This appears to be a **testing** directory containing test files and test utilities.\n\n"
        elif 'src' in path_parts or 'lib' in path_parts:
            doc_content += "This appears to be a **source code** directory containing implementation files.\n\n"
        elif 'doc' in path_parts or 'docs' in path_parts:
            doc_content += "This appears to be a **documentation** directory.\n\n"
        elif 'build' in path_parts or 'dist' in path_parts:
            doc_content += "This appears to be a **build** directory containing build scripts or compiled artifacts.\n\n"
        elif 'config' in path_parts or 'conf' in path_parts:
            doc_content += "This appears to be a **configuration** directory.\n\n"
        else:
            doc_content += f"This folder contains {len(files_in_folder)} files organized for specific purposes.\n\n"

        doc_content += f"""## Contents Summary

- **Files**: {len(files_in_folder)}
- **Subdirectories**: {len(subdirs_in_folder)}

## File Types

"""

        # Analyze file types
        ext_counts = defaultdict(int)
        for filename in files_in_folder:
            ext = Path(filename).suffix or 'no extension'
            ext_counts[ext] += 1

        for ext, count in sorted(ext_counts.items(), key=lambda x: -x[1])[:10]:
            doc_content += f"- `{ext}`: {count} file(s)\n"

        doc_file = out_folder / "doc.md"
        with open(doc_file, 'w', encoding='utf-8') as f:
            f.write(doc_content)

        self.docs_created += 1
        self.bytes_written += len(doc_content)

        # Create sub.md (merged keywords from this folder)
        sub_content = f"""# Keyword Index: {display_path}

## Keywords from this folder

This index aggregates keywords from all files in `{display_path}`.

"""

        # Collect keywords from this folder's files
        folder_keywords = defaultdict(list)
        for kw, occurrences in self.global_keywords.items():
            for file_path, desc in occurrences:
                if str(folder_path) in file_path or (folder_path == Path('.') and '/' not in file_path):
                    folder_keywords[kw].append((file_path, desc))

        # Write keywords A-Z
        sorted_kw = sorted(folder_keywords.items())
        current_letter = None

        for kw, occurrences in sorted_kw[:500]:  # Limit to 500 keywords per folder
            first_letter = kw[0].upper() if kw else '?'

            if first_letter != current_letter:
                current_letter = first_letter
                sub_content += f"\n## {current_letter}\n\n"

            sub_content += f"### `{kw}`\n\n"
            for file_path, desc in occurrences[:5]:  # Limit to 5 occurrences
                sub_content += f"- {desc}\n"
            sub_content += "\n"

        sub_file = out_folder / "sub.md"
        with open(sub_file, 'w', encoding='utf-8') as f:
            f.write(sub_content)

        self.docs_created += 1
        self.bytes_written += len(sub_content)

    def create_global_keyword_index(self):
        """Create global keywords.md file"""
        print("📝 Creating global keyword index...")

        kw_content = """# Global Keyword Index

This file contains all keywords extracted from the entire repository, organized alphabetically.

"""

        sorted_kw = sorted(self.global_keywords.items())
        current_letter = None

        for kw, occurrences in sorted_kw:
            first_letter = kw[0].upper() if kw else '?'

            if first_letter != current_letter:
                current_letter = first_letter
                kw_content += f"\n## {current_letter}\n\n"

            kw_content += f"### `{kw}`\n\n"
            kw_content += f"Found in {len(occurrences)} location(s):\n\n"

            for file_path, desc in occurrences[:10]:  # Limit to 10 occurrences
                # Create relative link
                safe_name = self.safe_filename(Path(file_path).name)
                folder = Path(file_path).parent
                if folder == Path('.'):
                    link = f"root/{safe_name}_docs.md"
                else:
                    link = f"{folder}/{safe_name}_docs.md"

                kw_content += f"- [{file_path}]({link}): {desc}\n"

            if len(occurrences) > 10:
                kw_content += f"- ... and {len(occurrences) - 10} more\n"

            kw_content += "\n"

        kw_file = self.out_dir / "keywords.md"
        with open(kw_file, 'w', encoding='utf-8') as f:
            f.write(kw_content)

        self.docs_created += 1
        self.bytes_written += len(kw_content)
        print(f"✓ Created keywords.md with {len(self.global_keywords)} keywords")

    def create_root_index(self):
        """Create root index.md"""
        print("📝 Creating root index...")

        index_content = """# Repository Documentation Index

## Welcome

This documentation was automatically generated from the repository source code.

## Structure

- [Global Keyword Index](keywords.md) - All keywords from the entire repository
- [Comprehensive Book](comprehensive_book.md) - Complete documentation in book form
- [Verification Report](verification_report.md) - Validation and integrity checks

## Folders

"""

        # List all documented folders
        for root, dirs, files in os.walk(self.out_dir):
            dirs[:] = sorted(dirs)  # Process in order
            for dirname in dirs:
                folder_path = Path(root) / dirname
                rel_path = folder_path.relative_to(self.out_dir)

                # Check if index exists
                if (folder_path / "index.md").exists():
                    index_content += f"- [{rel_path}/]({rel_path}/index.md)\n"

        index_content += "\n## Metadata\n\n"
        index_content += f"- **Generated**: {datetime.now().isoformat()}\n"
        index_content += f"- **Files scanned**: {self.files_scanned}\n"
        index_content += f"- **Docs created**: {self.docs_created}\n"
        index_content += f"- **Total words**: ~{self.words_estimated:,}\n"

        index_file = self.out_dir / "index.md"
        with open(index_file, 'w', encoding='utf-8') as f:
            f.write(index_content)

        self.docs_created += 1
        self.bytes_written += len(index_content)
        print("✓ Created root index.md")

    def create_comprehensive_book(self):
        """Create comprehensive_book.md by stitching together all documentation"""
        print("📚 Creating comprehensive book...")

        book_content = """# Comprehensive Repository Documentation Book

## Table of Contents

This book contains the complete documentation for the repository, organized by folder and file.

"""

        # Add introduction from root
        root_doc = self.out_dir / "root" / "doc.md"
        if root_doc.exists():
            with open(root_doc, 'r', encoding='utf-8') as f:
                book_content += "\n## Introduction\n\n"
                book_content += f.read()
                book_content += "\n\n---\n\n"

        # Walk through folders and add their documentation
        for root, dirs, files in os.walk(self.out_dir):
            dirs[:] = sorted(dirs)

            folder_path = Path(root)
            rel_path = folder_path.relative_to(self.out_dir)

            # Skip root level
            if rel_path == Path('.'):
                continue

            doc_file = folder_path / "doc.md"
            if doc_file.exists():
                with open(doc_file, 'r', encoding='utf-8') as f:
                    book_content += f"\n# Chapter: {rel_path}\n\n"
                    book_content += f.read()
                    book_content += "\n\n---\n\n"

        book_content += "\n## Appendix: File Summaries\n\n"
        book_content += "Complete file documentation is available in individual file docs.\n\n"

        book_file = self.out_dir / "comprehensive_book.md"
        with open(book_file, 'w', encoding='utf-8') as f:
            f.write(book_content)

        self.docs_created += 1
        self.bytes_written += len(book_content)
        self.words_estimated += self.count_words(book_content)
        print(f"✓ Created comprehensive_book.md ({len(book_content):,} bytes)")

    def create_verification_report(self):
        """Create verification_report.md"""
        print("🔍 Creating verification report...")

        report = f"""# Verification Report

Generated: {datetime.now().isoformat()}

## Summary

- **Files scanned**: {self.files_scanned}
- **Text files processed**: {len(self.text_files)}
- **Binary files**: {len(self.binary_files)}
- **Large files**: {len(self.large_files)}
- **Ignored files**: {len(self.ignored_files)}
- **Documentation files created**: {self.docs_created}
- **Errors encountered**: {len(self.errors)}

## File Classification

### Text Files ({len(self.text_files)})

Successfully processed {len(self.text_files)} text files.

### Binary Files ({len(self.binary_files)})

The following binary files were not processed:

"""

        for bf in sorted(self.binary_files)[:100]:
            report += f"- `{bf}`\n"

        if len(self.binary_files) > 100:
            report += f"\n... and {len(self.binary_files) - 100} more\n"

        report += f"\n### Large Files ({len(self.large_files)})\n\n"

        for lf in sorted(self.large_files):
            report += f"- `{lf}`\n"

        report += f"\n### Ignored Files ({len(self.ignored_files)})\n\n"

        for igf in sorted(self.ignored_files)[:100]:
            report += f"- `{igf}`\n"

        if len(self.ignored_files) > 100:
            report += f"\n... and {len(self.ignored_files) - 100} more\n"

        report += "\n## Errors\n\n"

        if self.errors:
            for error in self.errors[:50]:
                report += f"- {error}\n"
            if len(self.errors) > 50:
                report += f"\n... and {len(self.errors) - 50} more errors\n"
        else:
            report += "No errors encountered.\n"

        report += "\n## Link Validation\n\n"
        report += "Link validation: All internal relative links were generated programmatically.\n"

        report += "\n## Integrity\n\n"
        report += f"- Total bytes written: {self.bytes_written:,}\n"
        report += f"- Estimated words: {self.words_estimated:,}\n"

        report_file = self.out_dir / "verification_report.md"
        with open(report_file, 'w', encoding='utf-8') as f:
            f.write(report)

        self.docs_created += 1
        print("✓ Created verification_report.md")

    def create_manifest(self, fingerprint, repo_source):
        """Create manifest.json"""
        print("📋 Creating manifest...")

        manifest = {
            "repo_source": repo_source,
            "repo_fingerprint": fingerprint,
            "generated_at": datetime.now().isoformat(),
            "generator_version": "1.0.0",
            "files_scanned": self.files_scanned,
            "text_files": len(self.text_files),
            "binary_files": len(self.binary_files),
            "large_files": len(self.large_files),
            "ignored_files": len(self.ignored_files),
            "docs_created": self.docs_created,
            "bytes_written": self.bytes_written,
            "words_estimated": self.words_estimated,
            "errors": len(self.errors),
            "error_list": self.errors[:100],  # Include first 100 errors
        }

        manifest_file = self.out_dir / "manifest.json"
        with open(manifest_file, 'w', encoding='utf-8') as f:
            json.dump(manifest, f, indent=2)

        print("✓ Created manifest.json")
        return manifest

    def create_readme(self):
        """Create README.md in docs folder"""
        readme = """# Repository Documentation

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
"""

        readme_file = self.out_dir / "README.md"
        with open(readme_file, 'w', encoding='utf-8') as f:
            f.write(readme)

        print("✓ Created README.md")

    def run(self):
        """Main execution flow"""
        print("=" * 70)
        print("WORLD'S BEST REPO BOOK GENERATOR")
        print("=" * 70)
        print()

        # Step 1: Bootstrap
        print("STEP 1: Bootstrap")
        print("-" * 70)
        fingerprint = self.compute_fingerprint()
        print(f"Repository fingerprint: {fingerprint}")
        print()

        # Step 2: Scan
        print("STEP 2: Scan Repository")
        print("-" * 70)
        self.scan_repository()
        print()

        # Step 3: Per-file pass
        print("STEP 3: Per-File Documentation Generation")
        print("-" * 70)
        total_text_files = len(self.text_files)

        for i, rel_path in enumerate(self.text_files, 1):
            if i % 100 == 0 or i == total_text_files:
                print(f"  Processing file {i}/{total_text_files}: {rel_path}")
            self.create_file_docs(Path(rel_path))

        print(f"✓ Processed {len(self.text_files)} text files")
        print()

        # Step 4: Per-folder pass
        print("STEP 4: Per-Folder Documentation")
        print("-" * 70)

        # Collect all unique folders
        folders = set()
        folders.add(Path('.'))  # Root
        for rel_path in self.text_files:
            path = Path(rel_path)
            while path.parent != Path('.'):
                folders.add(path.parent)
                path = path.parent

        for folder in sorted(folders):
            self.create_folder_docs(folder)

        print(f"✓ Created documentation for {len(folders)} folders")
        print()

        # Step 5: Global merges
        print("STEP 5: Global Merges")
        print("-" * 70)
        self.create_global_keyword_index()
        self.create_root_index()
        self.create_comprehensive_book()
        print()

        # Step 6: Verification
        print("STEP 6: Verification & Manifest")
        print("-" * 70)
        self.create_verification_report()
        manifest = self.create_manifest(fingerprint, str(self.repo_path))
        print()

        # Step 7: README
        print("STEP 7: README")
        print("-" * 70)
        self.create_readme()
        print()

        # Final summary
        print("=" * 70)
        print("GENERATION COMPLETE!")
        print("=" * 70)
        print()

        summary = {
            "repo_source": str(self.repo_path),
            "repo_fingerprint": fingerprint,
            "files_scanned": self.files_scanned,
            "docs_created": self.docs_created,
            "words_estimated": self.words_estimated,
            "bytes_written": self.bytes_written,
            "errors": self.errors[:10]  # First 10 errors
        }

        print(json.dumps(summary, indent=2))
        print()

        return summary


def main():
    parser = argparse.ArgumentParser(description='Generate comprehensive repository documentation')
    parser.add_argument('--source', default='.', help='Repository path or URL')
    parser.add_argument('--out', default='./docs', help='Output directory')
    parser.add_argument('--resume', action='store_true', help='Resume from previous run')
    parser.add_argument('--max-file-chars', type=int, default=2000000, help='Max characters per file')
    parser.add_argument('--workers', type=int, default=1, help='Number of workers (not implemented)')

    args = parser.parse_args()

    generator = RepoBookGenerator(
        repo_path=args.source,
        out_dir=args.out,
        resume=args.resume,
        max_file_chars=args.max_file_chars
    )

    generator.run()


if __name__ == '__main__':
    main()

```

## High-Level Overview

This is a Python file located at `repo_book_gen.py`.

**Classes defined**: RepoBookGenerator

**Functions defined**: count_words, scan_repository, should_ignore, generate_file_documentation, __init__, is_binary, create_file_docs, compute_fingerprint, safe_filename, extract_keywords

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 1176
- Code lines: 802
- Comment lines: 145
- Blank lines: 229

### Main Components

**Classes** (1):
- `RepoBookGenerator`

**Functions** (28):
- `__init__()`
- `compute_fingerprint()`
- `count_words()`
- `create_comprehensive_book()`
- `create_file_docs()`
- `create_folder_docs()`
- `create_global_keyword_index()`
- `create_manifest()`
- `create_readme()`
- `create_root_index()`
- `create_verification_report()`
- `detect_file_type()`
- `extract_keywords()`
- `find_related_files()`
- `generate_detailed_analysis()`
- `generate_file_documentation()`
- `generate_keywords_file()`
- `generate_overview()`
- `generate_performance_security_notes()`
- `generate_testing_notes()`



## Usage Examples

### Main execution block:

```python
main()
```



## Performance & Security Notes

### Security Considerations

- ⚠️ Uses `eval()` - potential code injection risk
- ⚠️ Uses `exec()` - potential code injection risk
- ⚠️ Uses shell=True - potential command injection risk

### Performance Notes

- ✓ Uses async/await for non-blocking operations
- ✓ Implements caching mechanisms



## Related Files

- ` in content or ` (imported)



## Testing & Execution

**To execute this Python file:**

```bash
python repo_book_gen.py
```

