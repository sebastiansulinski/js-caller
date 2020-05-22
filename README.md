# JS Caller

Lightweight [axios](https://github.com/axios/axios) wrapper pre-configured with the following headers:

```javascript
'X-Requested-With': 'XMLHttpRequest'
Accept: 'application/json'
'Content-Type': 'application/json'
```

### Installation

```bash
npm i @ssdcode/js-caller
```

### Usage

```bash
import Caller from '@ssdcode/js-caller';

Caller.request(
  '/end-point',
  'post',
  { id: 1 },
  {
    timeout: 1000,
    headers: { 'X-Custom-Header': 'foobar' },
  }
);
```

`Caller.request` method takes 4 arguments:

```bash
- endpoint: request destination
- request method: get (default), post, put, patch, delete
- payload: data you wish to send with the request. If request method is in ['post', 'put', 'patch'] - payload will automaticaly be associated with 'data' index - otherwise 'params' will be used
- config: axios specific configuration
```

If you're using `csrf` token, make sure it is included as a meta tag and `js-caller` will fetch and attach it to the request automatically as a `X-CSRF-TOKEN` header.

```html
<meta name="csrf-token" content="{{ csrf_token() }}">
```