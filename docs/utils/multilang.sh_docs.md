# Documentation: utils/multilang.sh

## File Metadata

- **Path**: `utils/multilang.sh`
- **Size**: 3,484 bytes
- **Lines**: 165
- **Type**: Shell Script
- **Extension**: .sh


## Original Source Code

```bash
#!/usr/bin/env bash
#
# Usage example:
#     bash multilang.sh -a "binance fetchTicker XRP/USDT"
#

function usage() {
  echo "usage: $0 [-clsh] exchange method [...args]"
  echo "	-c      Number of lines to trim off the top and bottom of output"
  echo "	-l      View in less editor"
  echo "	-s      Remove special characters"
  echo "	-h      Display help"
  echo "	-v      Verbose mode"
  echo "	-k      Stacked"
  echo "	-t      Use table"
  exit 1
}

if [[ $# < 1 ]]; then
  usage
fi

cliFolder='./examples'

jsCli="${cliFolder}/js/cli.js"
pythonCli="${cliFolder}/py/cli.py"
phpCli="${cliFolder}/php/cli.php"

useLess=false
verbose=false
removeSpecial=false
numLines=0
stacked=false
useTable=false

function display {
  # Displays output in a less window or just to stdout
  if ${useLess}; then
    less -S -R
  else
    tee
  fi
}

function removeSpecial {
  # Removes special characters
  if ${removeSpecial}; then
    sed -e 's/\[[0-9]\{1,2\}m//g'
  else
    tee
  fi
}

function condense {
  # Trims output down to a set number of lines on the top and the bottom
  local pythonLength=$1
  local half=$(($numLines / 2))
  local continueFrom=
  if [ $half -gt $pythonLength ]; then
    continueFrom=${half}
  else
    continueFrom=$(($pythonLength - $half))
  fi
  if [ ${numLines} -gt 0 ]; then
    sed -n "1,${half}p;${continueFrom},${pythonLength}p"
  else
    tee
  fi
}

function removeAndColorLines {
  sed -E -e '/.*(iteration|^Array|^202.*|^$)/d' -e 's/  / /g' -e 's/  / /g' -e "s/(.*)/$(tput setaf $color)\1/"
}

function writeOutput {
  local interpretter="$1"
  local path="$2"
  local args="$3"
  if result=$($interpretter "$path" $args); then
    if ${verbose}; then
      echo "$interpretter completed" >&2
    fi
    removeSpecial <<< "$result" | removeAndColorLines $color
  else
    exit $?
  fi
}

function checkExitCode {
  if [ $? -ne 0 ]; then
    exit $?
  fi
}

function padOutput {
  local input="$1"
  local length="$2"
  echo "$input"
  lines=$(wc -l <<< "$input")
  toPad=$(($length - $lines))
  if [ $toPad -gt 0 ]; then
    yes "$(tput setaf 1)" | head -n $toPad
  fi
}

# Loop through command line arguments
while getopts 'hc:slvtk' flag; do
  case "${flag}" in
  h) usage ;;
  c) numLines="${OPTARG}" ;;
  s) removeSpecial=true ;;
  l) useLess=true ;;
  v) verbose=true ;;
  k) stacked=true ;;
  t) useTable=true ;;
  *) usage ;;
  esac
done

shift $((OPTIND - 1))

# if there are any unparsed options then print usage and exit
if grep -q -Ee "\s-[^0-9]" <<< "$@"; then
  usage
fi

if ${verbose}; then
  args="--verbose $@"
else
  args="$@"
fi

if ${useTable}; then
  table=""
else
  table="--no-table"
fi

jsArgs=$(<<< "$args" sed -E -e 's/(null|None)/undefined/g')
pythonArgs=$(<<< "$args" sed -E -e 's/(undefined|null)/None/g')
phpArgs=$(<<< "$args" sed -E -e 's/(undefined|None)/null/g')

color=3
jsOutput=$(writeOutput node $jsCli "${table} $jsArgs")
checkExitCode
((color++))

pythonOutput=$(writeOutput python3 $pythonCli "$pythonArgs")
checkExitCode
pythonLength=$(wc -l <<< "$pythonOutput")
((color++))

phpOutput=$(writeOutput php $phpCli "$phpArgs")
checkExitCode

if ${stacked}; then
  echo -e "$jsOutput\n$phpOutput\n$pythonOutput" | display
else
  # use padding here
  length=$(wc -l <<< "$phpOutput")
  jsOutput=$(padOutput "$jsOutput" $length)
  pythonOutput=$(padOutput "$pythonOutput" $length)
  paste <(echo "$jsOutput") <(echo "$phpOutput") <(echo "$pythonOutput") | column -s $'\t' -t | condense $pythonLength | display
fi

```

## High-Level Overview

This is a Shell Script file located at `utils/multilang.sh`.

**Functions defined**: writeOutput, usage, display, checkExitCode, removeSpecial, condense, removeAndColorLines, padOutput



## Detailed Walkthrough

### Code Structure

- Total lines: 165
- Code lines: 131
- Comment lines: 12
- Blank lines: 22

### Main Components

**Functions** (8):
- `checkExitCode()`
- `condense()`
- `display()`
- `padOutput()`
- `removeAndColorLines()`
- `removeSpecial()`
- `usage()`
- `writeOutput()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `${cliFolder}/php/cli.php` (referenced)
- `${cliFolder}/js/cli.js` (referenced)
- `${cliFolder}/py/cli.py` (referenced)



## Testing & Execution

**To execute this Shell Script file:**

```bash
bash utils/multilang.sh
```

