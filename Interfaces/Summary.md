 ## What Is an Interface?
 An interface provides a way of **specifying what methods an object should have**. It does not
specify how those methods should be **implemented**, though it may indicate (or at least hint at)
the semantics of the methods.

This allows you to group objects based on what features they provide. Functions that would normally expect an argument to be of a specific class
can instead be changed to expect an argument of a specific interface, allowing you to pass in
objects of any concrete implementation. It allows **unrelated objects to be treated identically**.

## extra
Duck typing was named
after the saying, “If it walks like a duck and quacks like a duck, it’s a duck.” It is a technique to
determine whether an object is an instance of a class based solely on **what methods it implements**,
but it also works great for checking whether a class **implements an interface**.

## Benefits of Using Interfaces
- If you are familiar with a certain interface, you
already know how to use any class that implements it
- Interfaces also stabilize the ways in which different classes can communicate.
- It also allows
you to specify in advance what features and operations you want a class to have.
- Testing and debugging become much easier.
- Using interfaces makes these
easier to find because explicit errors with useful messages are given if an object does not seem
to be of the expected type or does not implement the required methods. Logic errors are then
limited to the **methods themselves**, instead of the **object’s composition**.

## Drawbacks of Using Interfaces
- Using interfaces is a way of partially enforcing
strict typing. This reduces the **flexibility** of the language.
- JavaScript does not come with **built-in** support for interfaces,
- Using any interface implementation in JavaScript will create a small **performance hit**, due
in part to the overhead of having another method invocation. If this is a concern, you could always strip
this code out after development or tie it to a debugging flag so it is not executed in **production
environments**.
- The biggest drawback is that there is no way to force other programmers to **respect** the
interfaces you have created.

## How to Use the Interface Class
> The most important step (and the one that is the most difficult to perform) is to determine
whether it is worth using interfaces in your code. Small and less difficult projects may not
benefit from the added complexity that interfaces bring. It is up to you to determine whether
the benefits outweigh the drawbacks.

1. Include the Interface class in your HTML file. The Interface.js file is available at the eg5.
2. Go through the methods in your code that take in objects as arguments. Determine what
methods these object arguments are required to have in order for your code to work.
3. Create Interface objects for each discreet set of methods you require.
4. Remove all explicit constructor checking. Since we are using duck typing, the type of
the objects no longer matters.
5. Replace constructor checking with Interface.ensureImplements.

**these steps are illustrated at eg7**

## Patterns That Rely on the Interface
- The factory pattern
- The composite pattern
- The decorator pattern
- The command pattern

## Summary
We showed that all different implementations of the concept of the
interface share a couple features: a way of specifying **what methods to expect**, and a way to check
that those methods are **indeed implemented**, with helpful error messages if they are not.But careful use of the
Interface class can create more **robust** classes and more **stable** code.