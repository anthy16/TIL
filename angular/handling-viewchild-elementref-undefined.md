# Handling ViewChild ElementRef Undefined

A common issue I've found when making changes to a component using `@ViewChild`, is that the `ElementRef` suddenly returns undefined. This will happen if the element no longer gets set when the DOM is loaded - for example if the element is suddenly hidden behind an `*ngIf`.

Let's say that we have a div that is referenced in our typescript as `@ViewChild('element') element: ElementRef;` and that our html template only contains the following:

```html
<div #element>this is my div</div>
```

When the component is loaded, `element` will automatically be set after the view has been initialised. However, if we now hide it behind a parent div with an `*ngIf` statement:

```html
<div *ngIf="false">
  <div #element>this is my div</div>
</div>
```

Our element never gets set - because `*ngIf` returns false, thereby never showing the div within, referenced by `@ViewChild`.

A good way of dealing with this, is ensuring that the ViewChild is only referenced _after_ being set. You can do this by adding a setter:

```ts
private element: ElementRef;

  @ViewChild('element') set content(content: ElementRef) {
     if(content) { // initially setter gets called with undefined
          this.element = content;
     }
  }
```

A different option is to replace your `*ngIf` with `[hidden]`. The "hidden" flag only hides DOM content - it doesn't completely leave it out like `*ngIf` does.
