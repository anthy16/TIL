# Support Dark-Mode

CSS has a decently supported (according to [Can I Use](https://caniuse.com/?search=prefers-color-scheme)) media query, to switch styles based on whether the user client prefers light- or dark-mode.

Styling can be switched with the following query:
```css
@media (prefers-color-scheme: dark) {
  /* dark-mode styles */
  /* perhaps changing some custom properties */
}

@media (prefers-color-scheme: light) {
  /* light-mode styles */
  /* perhaps changing some custom properties */
}
```

Check [`prefers-color-scheme`](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme) for full documentation.