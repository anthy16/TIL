# Type Narrowing Using Structural Subtyping

TypeScript is not nominally typed, like C# or Java. Instead, TypeScript using [structural typing](https://www.typescriptlang.org/docs/handbook/type-compatibility.html). This means that in TypeScript, types can be related solely based on their members.

Due to this, the following code is valid in TypeScript:

```javascript
interface Pet {
  name: string;
}

class Dog {
  name: string;
}

let pet: Pet;

pet = new Dog(); // OK, because of structural typing
```

Similarly, the structural typing capabilities of TypeScript can be used for [type narrowing](https://www.typescriptlang.org/docs/handbook/2/narrowing.html).

First, let us expand our `Pet` interface, with the following properties:

```javascript
interface Pet {
  name: string;
  tricks: any[];
  color: string;
}
```

Then, let's say we have a function, `petDog` that takes one parameter; an object with one (string) key - `name`. 

Even though our `Pet` type doesn't match exactly, the type of `petDog`'s parameter is a subset of `Pet` and it is therefore possible to _narrow_ the type.

```javascript
const petDog = ({ name }: { name: string }) => {
  console.log(`Petting ${dog.name}. What a good boy!`);
};

let pet: Pet = { name: "bob", tricks: ['sit'], color: 'brown' };

petDog(pet);
// "Petting bob. What a good boy!"
```
