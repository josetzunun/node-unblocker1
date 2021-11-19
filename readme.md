# unblocker

Unblocker was originally a web proxy for evading internet censorship, similar to CGIproxy / PHProxy / Glype but
written in node.js. It's since morphed into a general-purpose library for proxying and rewriting remote webpages.

All data is processed and relayed to the client on the fly without unnecessary buffering, making unblocker one of the
fastest web proxies available.

[![Build Status](https://travis-ci.org/nfriedly/node-unblocker.svg?branch=master)](https://travis-co.org/nfriedly/node-unblocker)
[![npm-version](https://img.shields.io/npm/v/unblocker.svg)](https://www.npmjs.com/package/unblocker)

### The magic part

The script uses "pretty" urls which, besides looking pretty, allow links with relative paths
to just work without modification. (E.g. `<a href="path/to/file2.html"></a>`)

In addition to this, links that are relative to the root (E.g. `<a href="/path/to/file2.html"></a>`)
can he handled without modification by checking the referrer and 307 redirecting them to the proper
location in the referring site. (Although the proxy does attempt to rewrite these links to avoid the redirect.)

Cookies are proxied by adjusting thier path to include the proxy's URL, and a bit of extra work is done to ensure they
remain intact when switching protocols or subdomains.

### Limitations

Although the proxy works well for standard login forms and even most AJAX content, OAuth login forms and anything that uses
[postMessage](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) (Google, Facebook, etc.) are not
likely to work out of the box. This is not
WIP
