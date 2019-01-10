## How to using the Composite Pattern?
1. A composite implements **the same operations** as its constituent
objects. Executing one of these operations on the composite **passes it down to all of its children**. Each one then executes the same operation.
2. All composite objects implement a method that **fetches its children**. Using this method allows you to keep the implementation hidden and organize the children in any way you want. Any code that uses this object will not be dependant on your internal implementation.

## Benefits of the Composite Pattern
1. Simple operations can produce complex results with the composite. Instead of creating a lot of glue code to manually traverse arrays and other data structures, you can simply call an operation
on the **top-level** object and let each sub-object worry about how to pass it on. This is especially useful when you call these operations repeatedly.
2. Objects within a composite are very **loosely coupled**. As long as all objects within a composite implement the same interface, moving them around or interchanging them is a trivial operation. This improves code reuse and allows easier refactoring.
3. **Composite objects make excellent hierarchical structures**. Every time you execute an operation on a top-level composite, you are essentially performing a depth-first search on the entire structure to find the nodes. All of this is transparent to the programmer instantiating the object. It is very easy to add, remove, and find nodes within the hierarchy.

## Drawbacks of the Composite Pattern
1. The composite’s ease of use can mask the cost of each of the operations it supports. Because of the fact that any operation called on a composite is passed on to all of its children, **performance can suffer if the hierarchy is too large**.
2. It isn’t **immediately obvious** to a programmer that
calling a method such as topGallery.show() will instigate a complete traversal of a tree; good
**documentation** is very helpful in this situation.
3. In these examples, the rules governing the use of HTML must also apply to your composites. For example, it is
4. HTML tag have some nest rule, and These restrictions make your composite objects less useful and reduce some of the modularity of the code. Be sure to **weigh the benefits** against the costs when using a composite in this manner.
5. Some form of interface is required for composites to work properly. **The stricter the interface check**, the more reliable your composite class will be. This adds complexity to the system, but not a lot. If you are already using some form of interface or duck typing (such as the Interface class), this won’t be a problem. If you aren’t, you will have to incorporate type checking into your code.

## Summary
If used properly, the composite can be an extremely powerful pattern. It organizes sub-objects
into trees and allows operations to be executed upon these trees with a single command. It
improves the modularity of your code and allows for easy refactoring and swapping of objects.
It can be particularly well-suited to dynamic HTML user interfaces, allowing you to develop
code without having to know the final configuration of the user interface. It is one of the most
useful patterns to any JavaScript programmer.