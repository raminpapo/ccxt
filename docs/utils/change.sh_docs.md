# Documentation: utils/change.sh

## File Metadata

- **Path**: `utils/change.sh`
- **Size**: 725 bytes
- **Lines**: 18
- **Type**: Shell Script
- **Extension**: .sh


## Original Source Code

```bash
#!/usr/bin/env bash
previous_tag=0
for current_tag in $(git tag --sort=-creatordate)
do
    major_version=$(echo ${current_tag} | cut -d '.' -f 1)
    major_version=$(echo "$major_version" | sed -e "s/v//")
    if [ "$major_version" -ge 4 ] ;then
        if [ "$previous_tag" != 0 ]; then
            tag_date=$(git log -1 --pretty=format:'%ad' --date=short ${previous_tag})
            printf "## ${previous_tag} (${tag_date})\n\n"
            git log ${current_tag}...${previous_tag} --pretty=format:'*  %s [%h](https://github.com/ccxt/ccxt/commits/%H)' --reverse | grep -v Merge | grep -v skip | grep -v '-'
            # print $commits
            printf "\n\n"
        fi
        previous_tag=${current_tag}
    fi

done
```

## High-Level Overview

This is a Shell Script file located at `utils/change.sh`.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 2
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Shell Script file:**

```bash
bash utils/change.sh
```

