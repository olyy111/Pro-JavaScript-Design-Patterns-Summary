## What is Singleton Pattern
This is a broadly defination, it is an object that is used to namespace and group
together a **related set** of methods and attributes, and if it is instantiable at all, it can only be
instantiated once.

## Benefits of the Singleton Pattern
1. The main benefit of the singleton pattern is **the way it organizes your code**. By grouping related
methods and attributes together in a single location, which **can’t be instantiated multiple
times**, you can make it easier to debug and maintain your code.
2. Using descriptive namespaces also makes your code self-documenting and easier for novices to **read and understand**.
3. Sandboxingyour methods within a singleton **shields** them from being accidentally overwritten by other programmers and prevents the global namespace from becoming **cluttered** with variables.
4. It **separates** your code from third-party library or ad-serving code, allowing greater stability to the page as a whole.
5. **Lazy instantiation** allows you to create objects only as needed, reducing memory (and potentially bandwidth) consumption for users who don’t need them.
6. **Branching** allows you to create efficient methods, regardless of browser or environment incompatibilities. By assigning object literals based on the conditions at run-time, you can create methods tailored to a particular environment without having to waste cycles checking the environment again each time a method is called.

## Drawbacks of the Singleton Pattern
1. By providing a single point of access, the singleton pattern has the potential to tightly couple, There are times when it is better to **create an instantiable class, even if it is only ever instantiated once**. It also makes your code harder to unit test because it has the potential to tightly couple classes together.
2. It also makes **your code harder to unit test** because it has the potential to tightly
couple classes together. You can’t independently test a class that calls methods from a singleton;
instead, you must test the class and the singleton together as one unit.
3. Singletons are best
reserved for **namespacing** and for **implementing branching methods**. In these cases, coupling
isn’t as much of an issue.

## Notice
There are times when a more advanced pattern is better suited to the task. A virtual proxy
can be used instead of a lazy loading singleton when you want a little more control over how
the class gets instantiated. A true object factory can be used instead of a branching singleton
(although that factory may also be a singleton). Don’t be afraid to investigate the more specific
patterns in this book, and don’t settle on using a singleton just because it is “good enough.”
Make sure that the pattern you choose is **right for the job**.

## Summary
1. Not only is it useful
by itself, as we have seen in this chapter, but it can be used in some form or another with
most of the patterns in this book.
2. By putting your code within a singleton, you are going a long way
toward creating an API that can be used by others without fear of having their global variables
overwritten.