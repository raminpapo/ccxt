# Documentation: ts/src/static_dependencies/proxies/agent-base/README.md

## File Metadata

- **Path**: `ts/src/static_dependencies/proxies/agent-base/README.md`
- **Size**: 3,585 bytes
- **Lines**: 96
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
agent-base
==========
### Turn a function into an [`http.Agent`][http.Agent] instance

This module is a thin wrapper around the base `http.Agent` class.

It provides an abstract class that must define a `connect()` function,
which is responsible for creating the underlying socket that the HTTP
client requests will use.

The `connect()` function may return an arbitrary `Duplex` stream, or
another `http.Agent` instance to delegate the request to, and may be
asynchronous (by defining an `async` function).

Instances of this agent can be used with the `http` and `https`
modules. To differentiate, the options parameter in the `connect()`
function includes a `secureEndpoint` property, which can be checked
to determine what type of socket should be returned.

#### Some subclasses:

Here are some more interesting uses of `agent-base`.
Send a pull request to list yours!

 * [`http-proxy-agent`][http-proxy-agent]: An HTTP(s) proxy `http.Agent` implementation for HTTP endpoints
 * [`https-proxy-agent`][https-proxy-agent]: An HTTP(s) proxy `http.Agent` implementation for HTTPS endpoints
 * [`pac-proxy-agent`][pac-proxy-agent]: A PAC file proxy `http.Agent` implementation for HTTP and HTTPS
 * [`socks-proxy-agent`][socks-proxy-agent]: A SOCKS proxy `http.Agent` implementation for HTTP and HTTPS

Example
-------

Here's a minimal example that creates a new `net.Socket` or `tls.Socket`
based on the `secureEndpoint` property. This agent can be used with both
the `http` and `https` modules.

```ts
import * as net from 'net';
import * as tls from 'tls';
import * as http from 'http';
import { Agent } from 'agent-base';

class MyAgent extends Agent {
  connect(req, opts) {
    // `secureEndpoint` is true when using the "https" module
    if (opts.secureEndpoint) {
      return tls.connect(opts);
    } else {
      return net.connect(opts);
    }
  }
});

// Keep alive enabled means that `connect()` will only be
// invoked when a new connection needs to be created
const agent = new MyAgent({ keepAlive: true });

// Pass the `agent` option when creating the HTTP request
http.get('http://nodejs.org/api/', { agent }, (res) => {
  console.log('"response" event!', res.headers);
  res.pipe(process.stdout);
});
```

License
-------

(The MIT License)

Copyright (c) 2013 Nathan Rajlich &lt;nathan@tootallnate.net&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

[http-proxy-agent]: ../http-proxy-agent
[https-proxy-agent]: ../https-proxy-agent
[pac-proxy-agent]: ../pac-proxy-agent
[socks-proxy-agent]: ../socks-proxy-agent
[http.Agent]: https://nodejs.org/api/http.html#http_class_http_agent

```

## High-Level Overview

This is a Markdown file located at `ts/src/static_dependencies/proxies/agent-base/README.md`.

**Classes defined**: that, MyAgent

**Functions defined**: may, includes, into

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 96
- Code lines: 69
- Comment lines: 10
- Blank lines: 17

### Main Components

**Functions** (3):
- `includes()`
- `into()`
- `may()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `net` (imported)
- `http` (imported)
- `agent-base` (imported)
- `tls` (imported)



## Testing & Execution

**To execute this Markdown file:**

