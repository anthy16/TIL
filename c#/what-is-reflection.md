# What Is Reflection?

Reflection allows you to write code that can inspect metadata within the code itself. It allows types to provide information about themselves, during runtime.

To understand reflection there are a few things to understand about modules, types and members:

* Assemblies contain modules
* Modules contain types
* Types contain members

A program reflects on itself when it extracts metadata from its assemblies, then uses it to modify its own behavior or inform the user.

Here's a few examples of reflection:

1. Using `typeof()` checks the type of an object at runtime
2. Inspecting attributes of an object at runtime

[source](https://stackify.com/what-is-c-reflection/)