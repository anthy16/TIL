# Handling Breakpoints With Mixins

Oftentimes, a website will need to change appearance, based on the current screen size. I like to break my website layout down three times. One for mobile, one for tablets and one for desktop.

Using the following code, a mixin - `respond-to` - gets created and a list of breakpoints get set in an SCSS variable. `respond-to` takes an entry from this list and breaks down when reaching `max-width`. Should a value be used that isn't contained withing `$breakpoints`, the mixin will issue a warning. 

```scss
$breakpoints: (
  "sm": 767px,
  "md": 992px,
  "lg": 1200px,
) !default;

@mixin respond-to($breakpoint) {
  // If the key exists in the map
  @if map-has-key($breakpoints, $breakpoint) {
    // Prints a media query based on the value
    @media (max-width: map-get($breakpoints, $breakpoint)) {
      @content;
    }
  }

  // If the key doesn't exist in the map
  @else {
    @warn "Unfortunately, no value could be retrieved from `#{$breakpoint}`. "
          + "Available breakpoints are: #{map-keys($breakpoints)}.";
  }
}
```

The mixin can be used in the following way:

```scss
.container {
    display: flex;
    
    @include respond-to('sm') {
        flex-direction: column;
    }
}
```

In the example above, the class `container` will set `flex-direction: column` once the screen gets below `767px` - ie the variable value for "sm".

[source](https://css-tricks.com/snippets/sass/mixin-manage-breakpoints/)
