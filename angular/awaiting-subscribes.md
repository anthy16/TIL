# Awaiting Subscribes

Sometimes it is necessary to await a subscribe. You might be doing an `HttpClient` call that will return a value your application needs before it can continue. You used to be able to append your subscribes with `.toPromise()` but this is no longer valid in `RxJs 8` and onwards.

Instead, `firstValueFrom` and `lastValueFrom` have been introduced, doing essentially the same thing.

Here's an example: You have a product service that has a function `getProducts()` which returns all products. You need these to be loaded before doing anything else. In other words, you have to await the result. Here's an example of how to achieve that with `lastValueFrom`:

```typescript
public async loadProducts(): void {
    const products$ = this.productService.getProducts();
    this.products = await lastValueFrom(products$);
}
```

We await the http call in `productService` and wait for the stream to complete. We then set `this.products` to equal the result.

[source](https://indepth.dev/posts/1287/rxjs-heads-up-topromise-is-being-deprecated)