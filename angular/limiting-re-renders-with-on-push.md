# Limiting Re-renders with OnPush

Angular's default change detection strategy will continually check components for changes, even if no changes occurred. All components are checked, one after another, once per cycle. Changed detection performance can be described in the following way:

```
change detection performance = (time to check a change) * (number of changes)
```

`Time to check a change` is optimized internally by Angular itself. The parameter we can control is when to check for changes, i.e. `number of changes`.

One way to minimize number of calls is by using the `OnPush` change detection strategy. A component can be set to use the `OnPush` strategy in the following way:

```typescript
@Component({
  selector: "app-root",
  template: `<div>...</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush,
})
class AppComponent {
  // ...
}
```

By setting this change detection strategy, Angular will only run a change detection cycle on that specific subtree if an `@Input()` changes - or a component is marked for a check (async pipes will also mark the component to be checked). This will not work if we pass a mutable object and only change the values of said object. The object itself must change.

Because of this, `OnPush` makes a lot of sense in [presentational components](https://generic-ui.com/blog/enterprise-approach-to-the-smart-and-dumb-components-pattern-in-angular).

[source](https://www.thinktecture.com/en/angular/whats-the-hype-onpush/)
