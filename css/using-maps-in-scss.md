# Using Maps in SCSS

Maps are a way of bundling key-value pairs together in SCSS. Below is an example of a map of breakpoints:

```scss
$breakpoints: (
  "sm": 767px,
  "md": 992px,
  "lg": 1200px,
);
```

These values can then be accessed using the `map-get` or `map` functions:

```scss
@media (max-width: map-get($breakpoints, "sm")) {
    // ...
  }
}
```

[Source](https://sass-lang.com/documentation/values/maps)
