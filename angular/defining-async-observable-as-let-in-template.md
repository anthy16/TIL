# Defining Async Observable As `let` In Template

An observable from your `component.ts` can be used directly in your template by using Angular's inbuilt `async` pipe. The resulting value from said observable can then be defined as a variable itself, which you can use directly in the template:

```html
<div *ngIf="someObservableVariable$ | async as someObservableVariable">
  {{someObservableVariable.text}}
</div>
```

[source](https://angular.io/api/common/AsyncPipe)