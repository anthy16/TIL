# What Counts as Cross-Origin with CORS?

HTTP defines an [origin](https://developer.mozilla.org/en-US/docs/Glossary/origin) by the _scheme_ (HTTP/HTTPS, aka protocol), _hostname_ (domain), and _port_ of the URL used to access it. In order for two objects to have the same origin, all these aspects must match. It should be noted that _path_, i.e. everything following the origin, does not have to be the same.

[CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) (Cross-Origin Resource Sharing) uses these definitions of origin to determine whether something qualifies as _same-origin_ or _cross-origin_.

Below is a couple examples of _cross-origin_:

- `https://example.com` vs `http://example.com` (different scheme)
- `https://example.com` vs `https://sub.example.com` (different host)
- `https://example.com:3000` vs `https://example.com:5000` (different port)
