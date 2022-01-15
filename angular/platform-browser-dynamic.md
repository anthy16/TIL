# platformBrowserDynamic

The following line can be found in `main.ts` when creating a new Angular project:

```javascript
platformBrowserDynamic().bootstrapModule(AppModule);
```

Breaking the statement down, `platformBrowserDynamic()` is used to create a [Platform](https://angular.io/api/core/PlatformRef) which the Angular docs describe as:

> "the entry point for Angular on a web page"

`bootstrapModule()` is then called on the newly created platform, using `AppModule` as a parameter. This function creates an instance of the given `@NgModule`.