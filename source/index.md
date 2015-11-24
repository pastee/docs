---
title: Paste.ee API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://paste.ee/account/api'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - pastes
  - syntaxes
  - users
  - errors

search: true
---

# Introduction

Welcome to the Paste.ee API! You can use our API to access Paste.ee endpoints, which can get and submit pastes, and various other information like syntaxes.

We currently have no language bindings, if you'd like to submit one, please open an issue on (https://github.com/pastee/pastee)[Github]

<aside class="warning">The whole API is HTTPS only. If you need HTTP, you'll have to write your own proxy script.</aside>

# Authentication

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Access-Key: meowmeowmeow"

curl "api_endpoint_here?key=meowmeowmeow"

curl "api_endpoint_here"
  -d "key=meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Paste.ee uses Application keys to allow access to the API. You can register a new Application key at your [account api page](https://paste.ee/account/api).

Paste.ee expects for the API key to be included in all API requests to the server in a header that looks like the following:

`X-Auth-Token: meowmeowmeow`

Or in a query parameter/request body:

`key=meowmeowmeow`

Or as the username in basic auth:

`Authorization: Basic base64('meowmeowmeow:')`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal application/user application key.
</aside>
