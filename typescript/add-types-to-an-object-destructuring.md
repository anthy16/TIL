# Add Types To An Object Destructuring

For better readability, destructuring an object is often useful. An example of this could be a login form, where the user has to write his username and password.

We then want these two values to be typed - they would both be strings in this case. Knowing the normal way of adding types to objects in TS, you would think the solution would be to do as below:

```javascript
const { username: string, password: string } = loginFormValues;
```

But this conflicts with the [destructured renaming](https://wesbos.com/destructuring-renaming) ES6 feature. Instead of adding types, you would actually be renaming the object keys (in the example above, ES6 would think that both should be renamed to string, which obviously causes issues).

The correct way to achieve a strongly typed object destructuring would be to do as below:

```javascript
const { username, password }: { username: string, password: string } =
  loginFormValues;
```

[source](https://flaviocopes.com/typescript-object-destructuring/)