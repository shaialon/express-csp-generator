# Content Security Policy Generator, Powered by [RapidSec](https://rapidsec.com?utm_source=npm_csp_generator&utm_medium=readme)

Content Security Policy (CSP) helps prevent unwanted content from being injected/loaded into your webpages. This can mitigate cross-site scripting (XSS) vulnerabilities, Clickjacking, Formjacking, malicious frames, unwanted trackers, client-side injected malware, and other [web client-side attacks](https://rapidsec.com/docs/client-side-attacks?utm_source=npm_csp_generator&utm_medium=readme).

## Getting started with CSP - create your report-uri and first CSP on RapidSec

Go to [RapidSec and generate your first CSP](https://rapidsec.com/csp-automation?utm_source=npm_csp_generator&utm_medium=readme).
Choose a JSON export, that works with this specific express middleware.<br/>
You could otherwise use the [RapidSec Node.js MicroAgent](https://www.npmjs.com/package/@rapidsec/node) which is even more automatic.

<img src="https://user-images.githubusercontent.com/3126207/109227014-50575f80-77c8-11eb-97d7-3cdacf183c3d.gif" width="700"/>

## Install this package in your Express project

`npm install express-csp-generator`
or
`yarn add express-csp-generator`

## Add the report-only policy that you generated on RapidSec to send violation data to the report-uri:

```javascript
const contentSecurityPolicy = require("express-csp-generator");

app.use(
  contentSecurityPolicy({
    directives: {
      "frame-ancestors": ["'none'"],
      "block-all-mixed-content": [],
      "default-src": ["'none'"],
      "script-src": ["'self'", "'report-sample'"],
      "style-src": ["'self'", "'report-sample'"],
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
      "report-uri": [
        "https://gate.rapidsec.net/YOUR_SPECIFIC_RAPIDSEC_ENDPOINT",
      ],
    },
    reportOnly: true,
  })
);
```

## Now visit your local/ deployed site

You should see "Report-Only" CSP violations in your browser.
See example from Google.com (if implementing the middleware with RapidSec's Generated CSP):<br/>
<img src="https://user-images.githubusercontent.com/3126207/109227786-8c3ef480-77c9-11eb-8315-c151deb05ebe.png" width="700"/>

## Use the CSP builder to generate your CSP based on the reports

See your new CSP violations quickly from the menu bar and easily Allow or Dismiss them by CSP directive.
Includes explanations on the meaning of each directive.
<img src="https://user-images.githubusercontent.com/3126207/109228319-51898c00-77ca-11eb-8281-accdd1e94e0d.gif" width="700"/>

## Deploy versions of your CSP

Once you've allowed the appropriate assets, click "Build CSP", to generate a new version of your `content-security-policy`.<br/>

## See In-depth Analytics

Explore your CSP reports. Dig into your data. Slice and dice by multiple parameters. Understand which assets / pages / browsers are generating CSP violations, and access a detailed report view.
<img src="https://user-images.githubusercontent.com/3126207/109228314-4fbfc880-77ca-11eb-9c2a-603ac37d4b00.gif" width="700"/>

## Get Reports

Deployed your Report-Only CSP and now your users covered some additional flows with some additional browsers?<br/>
You'll get an email with a summary of your new pending review CSP violations.
<img src="https://user-images.githubusercontent.com/3126207/109228310-4e8e9b80-77ca-11eb-8394-9da0116cf021.png" width="700"/>

## Note

This Express middleware does minimal validation on the CSP integrity and quality, and relies that you're [generating proper CSPs via RapidSec](https://rapidsec.com/csp-automation?utm_source=npm_csp_generator&utm_medium=readme). If you choose to build your CSP manually - use a more sophisticated CSP validator, like [CSP Scanner](https://cspscanner.com/?utm_source=npm_csp_generator&utm_medium=readme) to make sure your CSP is both valid, and effective at mitigating attacks.

## See also

- [RapidSec CSP Generator](https://rapidsec.com/csp-automation?utm_source=npm_csp_generator&utm_medium=readme)
- [CSP Scanner](https://cspscanner.com/?utm_source=npm_csp_generator&utm_medium=readme)
- [CSP Scanner Chrome Extension](https://chrome.google.com/webstore/detail/csp-scanner-test-analyze/eoiiiomeoogcpnkdedcodoeaacpdfmdj)
- [CSP Bypasses](https://rapidsec.com/docs/csp-bypasses?utm_source=npm_csp_generator&utm_medium=readme)

## Legal

Original code modified from MIT licensed [Helmet-CSP](https://github.com/helmetjs/helmet/tree/main/middlewares/content-security-policy)
