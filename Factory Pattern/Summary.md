## difference between simple factory and factory pattern
we discussed the simple factory and the factory pattern. Using a bicycle shop
as an example, we illustrated the differences between the two; the simple factory encapsulates
instantiation, typically in **a separate class or object**, while the true factory pattern implements
an **abstract factory** method and **defers instantiation** to subclasses.

> eg1、eg2

## where the factory pattern should be applied?

1. Chief among those is when the type of class being
instantiated is known only at **run-time**, not at **development time**.

> createXhrObject 在eg3的实现


2. It is also useful when you have
many **related objects with complex setup costs**,This is especially true if the setup needs to be done only **once** for all instances
of a certain type of object. Putting the code for this setup in the class constructor is inefficient
because it will be called **even if the setup is complete** and because it decentralizes it among
the different classes. 

> createXhrObject 在eg3的实现

3. when you want to create a class with member
objects but still keep them relatively decoupled

> createFeedReader 在eg6的实现

## Benefits of the Factory Pattern
The main benefit to using the factory pattern is that you can **decouple objects**. Using a factory
method instead of the new keyword and a concrete class allows you to centralize all of the
instantiation code in one location.

All of these benefits are related to two of the object-oriented design principles:

- make your
objects loosely coupled
- prevent code duplication.

## Drawbacks of the Factory Pattern

Factory methods shouldn’t be used when there isn’t any chance of swapping
out a different class or when you don’t need to select interchangeable classes at run-time.

> be sure you don’t overuse them.
If in doubt, don’t use them; you can always refactor your code later to use the factory pattern.