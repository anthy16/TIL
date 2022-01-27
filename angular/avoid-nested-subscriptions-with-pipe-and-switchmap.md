# Avoid Nested Subscriptions With Pipe And SwitchMap

Sometimes nested subscriptions might seem like a good idea _(they're not)_ - at least on the surface.

An example of this could be the following - when a part of your state changes, you might want to create an HTTP request to some endpoint with that changed state. Maybe you have an id in your state that reflects an active product, and when that id changes, you need to let the backend know so that you can retrieve a list of similar products.

You could subscribe to the `store` and simply call your backend via `HttpClient` within that subscribe. But `HttpClient` calls are also observables that need to be subscribed. Which means you've now created a nested subscription.

Instead, we can use the `pipe` operator along with `switchMap` from `rxjs`:

```javascript
this.store.select((state) => selectActiveProduct(state)).pipe(
  switchMap(product => fetchSimilarProducts(product))
).subscribe(...)
```

[source](https://angular-checklist.io/default/checklist/rxjs/Z1eFwa9)
