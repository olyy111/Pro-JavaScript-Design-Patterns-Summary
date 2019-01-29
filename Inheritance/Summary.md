## When Should Inheritance Be Used?
1. By having classes or objects
inherit from each other, you only have to define a given method **once**.
2. By the same token, if
you ever have to make changes to this method or track down errors in it, the fact that it is defined
in a **single location** can save you a great deal of time and effort.

- Prototypal inheritance (with the clone function)
is best used in situations where **memory efficiency** is important.
- Classical inheritance (with
the extend function) is best used when the programmers dealing with the objects are familiar
with how inheritance works in other object-oriented languages.

Both of these methods are wellsuited
to **class hierarchies** where the differences between each class are slight.

- If the classes are
very different from each other, it usually makes more sense to augment them with methods from
**mixin classes**.