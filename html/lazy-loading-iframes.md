# Lazy Loading Iframes

An iframe - and sometimes more than one - can take up quite a few resources when loading. Luckily, lazy loading iframes have become [standardized](https://github.com/whatwg/html/pull/5579) in Chrome and Chromium-based browsers.

The following attribute can be added to the iframe tag:

```html
<iframe
  src="https://example.com"
  loading="lazy"
  width="600"
  height="400"
></iframe>
```

Where `loading="lazy"` signifies that the iframe should not be loaded until the user scrolls near it. A demo can be found [here](https://lazy-load.netlify.app/iframes/).

[source](https://web.dev/iframe-lazy-loading/)
