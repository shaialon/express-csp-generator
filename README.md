# Content Security Policy Generator, Powered by [RapidSec](https://rapidsec.com)

Content Security Policy (CSP) helps prevent unwanted content from being injected/loaded into your webpages. This can mitigate cross-site scripting (XSS) vulnerabilities, Clickjacking, formajacking, malicious frames, unwanted trackers, client-side injected malware, and other [web client-side attacks](https://rapidsec.com/docs/client-side-attacks).

## 1. Getting started with CSP - create your report-uri and first CSP on RapidSec
Go to [RapidSec and generate your first CSP](https://rapidsec.com/csp-automation).
Choose a JSON export, that works with this specific express middleware.<br/>
You could otherwise use the [RapidSec Node.js MicroAgent](https://www.npmjs.com/package/@rapidsec/node) which is even more automatic.

<img src="https://user-images.githubusercontent.com/3126207/109227014-50575f80-77c8-11eb-97d7-3cdacf183c3d.gif" width="600"/>

## 2. Install this package in your Express project
`npm install express-csp-generator`
or
`yarn add express-csp-generator`

## 3. Add the report-only policy that you generated on RapidSec to send sends violation data to the report-uri:

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

## 4. Visit your local/ deployed site
You should see "Report-Only" CSP violations in your browser.
See example from Google.com (if implementing the middleware with RapidSec's Generated CSP:<br/>
<img src="https://user-images.githubusercontent.com/3126207/109227786-8c3ef480-77c9-11eb-8315-c151deb05ebe.png" width="600"/>

## 5. Use the CSP builder to generate your CSP based on the reports
See your new CSP violations quickly from the menu bar and easily Allow or Dismiss them by CSP directive.
Includes explanations on the meaning of each directive.
<img src="https://user-images.githubusercontent.com/3126207/109228319-51898c00-77ca-11eb-8281-accdd1e94e0d.gif" width="600"/>

## 6. Deploy versions of your CSP.
Once you've allowed the appropriate assets, click "Build CSP", to generate a new version of your `content-security-policy`.<br/>
Copy the new JSON and add it to your code instead of the existing policy.
<img src="https://user-images.githubusercontent.com/3126207/109229704-59e2c680-77cc-11eb-846e-5d5ac5492642.gif" width="600"/>

## 7. See In-depth Analytics
Explore your CSP reports. Dig into your data. Slice and dice by multiple parameters. Understand which assets / pages / browsers are generating CSP violations, and access a detailed report view.
<img src="https://user-images.githubusercontent.com/3126207/109228314-4fbfc880-77ca-11eb-9c2a-603ac37d4b00.gif" width="600"/>

## 8. Get Reports 
Deployed your Report-Only CSP and now your users covered some additional flows with some additional browsers?<br/>
You'll get an email with a summary of your new pending review CSP violations.
<img src="https://user-images.githubusercontent.com/3126207/109228310-4e8e9b80-77ca-11eb-8394-9da0116cf021.png" width="600"/>

## Note
This Express middleware does minimal validation on the CSP integrity and quality, and relies that you're [generating proper CSPs via RapidSec].(https://rapidsec.com/csp-automation). If you choose to build your CSP manually - use a more sophisticated CSP validator, like [CSP Scanner](https://cspscanner.com/) to make sure your CSP is both valid, and effective at mitigating attacks. 

## See also
- [RapidSec CSP Generator](https://rapidsec.com/csp-automation)
- [CSP Scanner](https://cspscanner.com/)
- [CSP Scanner Chrome Extension](https://chrome.google.com/webstore/detail/csp-scanner-test-analyze/eoiiiomeoogcpnkdedcodoeaacpdfmdj)
- [CSP Bypasses](https://rapidsec.com/docs/csp-bypasses)

## Legal
Original code modified from MIT licensed [Helmet-CSP](https://github.com/helmetjs/helmet/tree/main/middlewares/content-security-policy)
