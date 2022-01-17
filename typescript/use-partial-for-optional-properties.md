# Use Partial<Type> For Optional Properties

Sometimes it might make sense to have a variable that only contains some properties of an existing type. 

As an example, let's say you have a model `Card`:

```javascript
interface Card {
    title: string,
    description: string,
    active: boolean
}
```

You want to create a function that takes a parameter of type `Card` along with a property of `Card` with a new value that needs to override the old property. The function then returns the updated `Card`. 

However, it might be any property, either `title`, `description` or `active`. So how do you achieve this? You could create an update function for each property that could potentially be updated, i.e. `updateTitle`, `updateDescription` and `updateActive`. But that can get messy and unneccessary - especially if the type has a lot of properties.

Instead of trying to come up with a complex solution to an easy problem - TypeScript has you covered with the [utility type](https://www.typescriptlang.org/docs/handbook/utility-types.html) `Partial`. Using Partial, you can define a specific type, where all properties are optional. This enables you to create the following update function:

```javascript
function updateCard(card: Card, fieldsToUpdate: Partial<Card>) {
    return {...card, ...fieldsToUpdate}
}
```

Which is a lot prettier, and a lot more simple.