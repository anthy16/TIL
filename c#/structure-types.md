# Structure Types

Also known as "struct type". An example of a struct implementation can be seen below (borrowed from [the official docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/struct)):

```c#
public struct Coords
{
    public Coords(double x, double y)
    {
        X = x;
        Y = y;
    }

    public double X { get; }
    public double Y { get; }

    public override string ToString() => $"({X}, {Y})";
}
```

Structure types are light-weight and can be useful instead of classes in certain cases. In contrast to classes that have _reference semantics_, structs have _value semantics_. The difference between the two is that a variable of a structure type contains the instance of the type. A variable of a reference type contains a reference to the instance of the type - not the instance itself. Structs can be useful if you need similar behaviour to a built-in data type.

Bill Wagner writes the following principles in his book ["Effective C#"](https://www.amazon.com/dp/0321245660):

> 1. Is the main responsability of the type data storage?
> 2. Is its public interface defined entirely by properties that access or modify its data members?
> 3. Are you sure your type will never have subclasses?
> 4. Are you sure your type will never be treated polymorphically?
>    If you answer 'yes' to all 4 questions: use a struct. Otherwise, use a class.

The official docs recommend structure types be used for small data-centric types with little or no behaviour. It is also recommended that structure types are defined as immutable. One way of doing this is by creating `readonly` structs, like below:

```c#
public readonly struct Coords
{
    public Coords(double x, double y)
    {
        X = x;
        Y = y;
    }

    public double X { get; init; }
    public double Y { get; init; }

    public override string ToString() => $"({X}, {Y})";
}
```