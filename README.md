# Content Security Policy Generator, Powered by [RapidSec](https://rapidsec.com)

Content Security Policy (CSP) helps prevent unwanted content from being injected/loaded into your webpages. This can mitigate cross-site scripting (XSS) vulnerabilities, Clickjacking, formajacking, malicious frames, unwanted trackers, client-side injected malware, and other [web client-side attacks](https://rapidsec.com/docs/client-side-attacks).

## Getting started with CSP - create your report-uri and first CSP on RapidSec
Go to [RapidSec and generate your first CSP](https://rapidsec.com/csp-automation).
Choose a JSON export, that works with this specific express middleware.<br/>
You could otherwise use the [RapidSec Node.js MicroAgent](https://www.npmjs.com/package/@rapidsec/node) which is even more automatic.

<img src="https://user-images.githubusercontent.com/3126207/109225564-1a18e080-77c6-11eb-8040-59ad6d8c4229.gif" width="700"/>

## Install this package in your Express project
`npm install express-csp-generator`
or
`yarn add express-csp-generator`

## Add the report-only policy that you generated on RapidSec to send sends violation data to the report-uri:

```javascript
const contentSecurityPolicy = require("express-csp-generator");

app.use(
  contentSecurityPolicy({
  "directives": {
    "frame-ancestors": ["'none'"],
    "block-all-mixed-content": [],
    "default-src": ["'none'"],
    "script-src": ["'self'","'report-sample'"],
    "style-src": ["'self'","'report-sample'"],
    "object-src": ["'none'"],
    "frame-src": ["'none'"],
    "child-src": ["'none'"],
    "img-src": ["'self'"],
    "font-src": ["'self'"],
    "connect-src": ["'none'"],
    "manifest-src": ["'none'"],
    "base-uri": ["'self'"],
    "form-action": ["'none'"],
    "media-src": ["'none'"],
    "prefetch-src": ["'none'"],
    "worker-src": ["'none'"],
    "report-uri": ["https://gate.rapidsec.net/YOUR_SPECIFIC_RAPIDSEC_ENDPOINT"]
  },
  "reportOnly": true
})
);
```

This middleware does minimal validation - You should use a more sophisticated CSP validator, like [CSP Scanner](https://cspscanner.com/) to make sure your CSP is both valid, and effective at mitigating attacks, or prefrabely, [generate your CSP on RapidSec](https://rapidsec.com/csp-automation).



## See also

- [CSP Scanner](https://cspscanner.com/)
- [CSP Bypasses](https://cspscanner.com/csp-bypasses)

## Legal
Original code modified from MIT licensed [Helmet-CSP](https://github.com/helmetjs/helmet/tree/main/middlewares/content-security-policy)
