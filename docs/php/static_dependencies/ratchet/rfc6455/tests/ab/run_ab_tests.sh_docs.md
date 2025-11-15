# Documentation: php/static_dependencies/ratchet/rfc6455/tests/ab/run_ab_tests.sh

## File Metadata

- **Path**: `php/static_dependencies/ratchet/rfc6455/tests/ab/run_ab_tests.sh`
- **Size**: 1,346 bytes
- **Lines**: 49
- **Type**: Shell Script
- **Extension**: .sh


## Original Source Code

```bash
set -x
cd tests/ab

if [ "$ABTEST" = "client" ]; then
  docker run --rm \
      -d \
      -v ${PWD}:/config \
      -v ${PWD}/reports:/reports \
      -p 9002:9002 \
      --name fuzzingserver \
      crossbario/autobahn-testsuite wstest -m fuzzingserver -s /config/fuzzingserver$SKIP_DEFLATE.json
  sleep 5
  if [ "$TRAVIS" != "true" ]; then
      echo "Running tests vs Autobahn test client"
      ###docker run -it --rm --name abpytest crossbario/autobahn-testsuite wstest --mode testeeclient -w ws://host.docker.internal:9002
  fi
  php -d memory_limit=256M clientRunner.php

  docker ps -a

  docker logs fuzzingserver

  docker stop fuzzingserver

  sleep 2
fi

if [ "$ABTEST" = "server" ]; then
  php -d memory_limit=256M startServer.php &
  sleep 3

  if [ "$OSTYPE" = "linux-gnu" ]; then
    IPADDR=`hostname -I | cut -f 1 -d ' '`
  else
    IPADDR=`ifconfig | grep "inet " | grep -Fv 127.0.0.1 | awk '{print $2}' | head -1 | tr -d 'adr:'`
  fi

  docker run --rm \
      -i \
      -v ${PWD}:/config \
      -v ${PWD}/reports:/reports \
      --name fuzzingclient \
      crossbario/autobahn-testsuite /bin/sh -c "sh /config/docker_bootstrap.sh $IPADDR; wstest -m fuzzingclient -s /config/fuzzingclient$SKIP_DEFLATE.json"
  sleep 1

  # send the shutdown command to the PHP echo server
  wget -O - -q http://127.0.0.1:9001/shutdown
fi

```

## High-Level Overview

This is a Shell Script file located at `php/static_dependencies/ratchet/rfc6455/tests/ab/run_ab_tests.sh`.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 37
- Comment lines: 2
- Blank lines: 10

### Main Components

**Constants** (1):
- `IPADDR`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `sh /config/docker_bootstrap.sh $IPADDR; wstest -m fuzzingclient -s /config/fuzzingclient$SKIP_DEFLATE.json` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
